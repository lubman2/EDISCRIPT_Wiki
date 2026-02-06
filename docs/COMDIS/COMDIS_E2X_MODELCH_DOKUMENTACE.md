# COMDIS EDI to XML Conversion Script
## Dokumentace: COMDIS_E2X_MODELCH.pcs

---

## 📋 Přehled

Skript **COMDIS_E2X_MODELCH.pcs** konvertuje EDIFACT COMDIS zprávy (Sales Forecasting) do strukturovaného XML formátu.

**Co skript dělá:**
1. Čte EDIFACT COMDIS soubor
2. Extrahuje všechny relevantní informace
3. Transformuje je do XML hierarchické struktury
4. Uloží XML soubor do adresáře `OUTPUT/`

---

## 🎯 Cílová XML Struktura

```xml
<?xml version="1.0" encoding="UTF-8"?>
<COMDIS>
  
  <!-- PART 1: HEADERS AND METADATA -->
  <Header>
    
    <!-- UNB - Interchange Control Header -->
    <Interchange>
      <SyntaxVersion>UNOD:3</SyntaxVersion>
      <Sender>8594195490002:14</Sender>
      <Receiver>8595149000001:14</Receiver>
      <InterchangeDate>251113</InterchangeDate>
      <InterchangeTime>2013</InterchangeTime>
      <InterchangeControlReference>590880426</InterchangeControlReference>
    </Interchange>
    
    <!-- UNH - Message Header -->
    <Message>
      <MessageType>COMDIS</MessageType>
      <Version>D</Version>
      <Release>01B</Release>
      <MessageReferenceNumber>530266478</MessageReferenceNumber>
    </Message>
    
    <!-- USH - Message Metadata -->
    <MessageMetadata>
      <TestIndicator>94W</TestIndicator>
      <RepeatingGroupNumber>1</RepeatingGroupNumber>
      <InterchangeControlType>2</InterchangeControlType>
    </MessageMetadata>
    
    <!-- BGM + DTM - Document Information -->
    <DocumentInfo>
      <DocumentType>67</DocumentType>
      <DocumentNumber>FP703632526</DocumentNumber>
      <DocumentStatus>9</DocumentStatus>
      <CreationDate>20251113</CreationDate>
    </DocumentInfo>
  </Header>
  
  <!-- PART 2: PARTIES (TRADING PARTNERS) -->
  <Parties>
    <Buyer>
      <GLN>8594195490002</GLN>
      <Name>Smarty CZ a.s.</Name>
    </Buyer>
    <Supplier>
      <GLN>8595149000001</GLN>
      <Name>AT Computers a.s.</Name>
    </Supplier>
  </Parties>
  
  <!-- PART 3: FORECAST PERIODS -->
  <!-- Každá USC (Unsolicited Commodity Schedule) = jedna perioda -->
  <!-- Každý LIN (Line item) = jeden produkt v periodě -->
  <ForecastPeriods>
    
    <Period index="0">
      <PeriodNumber>01643674</PeriodNumber>
      <StartDate>20251113</StartDate>
      
      <Items>
        <Item index="0">
          <LineItemNumber>1</LineItemNumber>
          <ProductNumber>PROD001</ProductNumber>
          <ProductDescription>Laptop Model X1</ProductDescription>
          <Quantity>100</Quantity>
          <Unit>PCE</Unit>
          <DeliveryDate>20251120</DeliveryDate>
        </Item>
        
        <Item index="1">
          <LineItemNumber>2</LineItemNumber>
          <ProductNumber>PROD002</ProductNumber>
          <ProductDescription>Mouse Wireless</ProductDescription>
          <Quantity>500</Quantity>
          <Unit>PCE</Unit>
          <DeliveryDate>20251120</DeliveryDate>
        </Item>
      </Items>
      
    </Period>
    
    <!-- Další periody... -->
    
  </ForecastPeriods>
  
  <!-- PART 4: CONTROL INFORMATION -->
  <Control>
    <SegmentCount>14</SegmentCount>
    <GroupCount>1</GroupCount>
    <MessageControlCount>1</MessageControlCount>
  </Control>
  
</COMDIS>
```

---

## 📊 EDIFACT → XML Mapping

| EDIFACT Segment | Popis | XML Element |
|---|---|---|
| **UNB** | Interchange Control Header | `/COMDIS/Header/Interchange` |
| **UNH** | Message Header | `/COMDIS/Header/Message` |
| **USH** | Message Metadata | `/COMDIS/Header/MessageMetadata` |
| **BGM** | Document/Message Name and Number | `/COMDIS/Header/DocumentInfo` |
| **DTM** | Date/Time/Period | `/COMDIS/Header/DocumentInfo/CreationDate` |
| **NAD** | Name and Address | `/COMDIS/Parties/Buyer\|Supplier` |
| **USC** | Unsolicited Commodity Schedule | `/COMDIS/ForecastPeriods/Period` |
| **UST** | Unsolicited Commodity Schedule Detail | Period metadata |
| **LIN** | Line Item | `/COMDIS/ForecastPeriods/Period/Items/Item` |
| **IMD** | Item Description | `Item/ProductDescription` |
| **QTY** | Quantity | `Item/Quantity` + `Item/Unit` |
| **DTM** | Delivery Date | `Item/DeliveryDate` |
| **CNT** | Control Total | `/COMDIS/Control/SegmentCount` |
| **UNZ** | Message/Interchange Control Summary | `/COMDIS/Control/MessageControlCount` |

---

## 🔧 PCS Skriptovací Operace

### Klíčové Funkce Použité:

#### 1. **XMLCREATE** - Vytvoření XML dokumentu
```pcs
XMLCREATE @0
```
Inicializuje nový XML dokument v objektu `@0`

#### 2. **XMLTAG** - Navigace/Vytvoření XML elementů
```pcs
XMLTAG @0 "COMDIS,0"              ; Vytvoří root element
XMLTAG @0 "Header,1"               ; Přidá child element
XMLTAG @0 "Period,3,#1"            ; Přidá element s indexem
```

#### 3. **XMLTEXTSET** - Nastavení textu elementu
```pcs
XMLTEXTSET @0 $3                   ; Vloží obsah $3 do aktuálního elementu
```

#### 4. **EDIGET** - Čtení EDIFACT segmentů
```pcs
EDIGET @0 $3 "UNB,1,1"             ; Čte segment UNB, pozice 1,1
EDIGET @0 $3 "NAD,2,1"             ; Čte NAD segment, pozice 2,1
EDIGET @0 $3 "LIN,1,1,,1,#2,,,#1" ; S loop počítadly #1, #2
```

#### 5. **IFEMPTY** - Kontrola prázdné hodnoty
```pcs
IFEMPTY $3 THEN SkipProductDesc    ; Skočí na label pokud je $3 prázdné
```

#### 6. **Smyčky** - Iterace přes segmenty
```pcs
LET #1=-1
LABEL NextPeriod
LET #1=#1+1
EDIGET @0 $3 "USC,1,1,,,#1"        ; Čte #1-tou USC
IFEMPTY $3 THEN EndPeriods
; ... zpracování ...
GOTO NextPeriod
LABEL EndPeriods
```

#### 7. **XMLSAVE** - Uložení XML na disk
```pcs
XMLSAVE @0 $2                      ; Uloží XML z @0 do souboru $2
```

---

## 🎛️ Proměnné Skriptu

| Proměnná | Typ | Popis |
|---|---|---|
| `$0` | String | Vstupní soubor (EDIFACT) |
| `$1` | String | Jméno souboru (bez cesty) |
| `$2` | String | Výstupní cesta XML souboru |
| `$3` | String | Pracovní proměnná - čtená data |
| `$4` | String | Pracovní proměnná - QTY/IMD |
| `$8` | String | Base path (PROGPATH) |
| `@0` | Object | EDI/XML objekt |
| `#1` | Numeric | Počítadlo period (USC) |
| `#2` | Numeric | Počítadlo položek (LIN) |

---

## 📝 Struktura Smyčky

```
ACTION 1
  └─ Inicializace (XML, cesty)
  │
  ├─ PART 1: Čtení UNB, UNH, USH
  │           ↓ XML: Header
  │
  ├─ PART 2: Čtení BGM, DTM
  │           ↓ XML: DocumentInfo
  │
  ├─ PART 3: Čtení NAD (Buyer, Supplier)
  │           ↓ XML: Parties
  │
  ├─ PART 4: Smyčka přes USC periody (#1)
  │           ├─ Smyčka přes LIN položky (#2)
  │           │  └─ Čtení IMD, QTY, DTM
  │           │     ↓ XML: ForecastPeriods/Period/Items/Item
  │           └─ Konec smyčky
  │
  ├─ PART 5: Čtení CNT, UNZ
  │           ↓ XML: Control
  │
  └─ XMLSAVE → Uložení výstupního souboru
```

---

## 🚀 Použití Skriptu

### Příkazová řádka (Windows):
```batch
ProcRun.exe -a1 -fCOMDIS_E2X_MODELCH.pcf -$0="C:\INBOX\comdis.edi"
```

### Variabilní parametry:
```batch
ProcRun.exe -a1 -fCOMDIS_E2X_MODELCH.pcf ^
  -$0="comdis_input.edi" ^
  -$8="D:\EDICOMRP\"
```

---

## 📤 Výstup

Skript vytvoří XML soubor v adresáři:
```
OUTPUT/COMDIS_<jméno_vstupního_souboru>.xml
```

**Příklad:**
- Input: `comdis_001.edi`
- Output: `OUTPUT/COMDIS_comdis_001.xml`

---

## 🔍 Struktura COMDIS EDIFACT

```
UNA:+.? '                    ← Syntax Character String
UNB...                       ← Interchange Header
  UNH+530266478+COMDIS:D:01B:UN:EAN003'
    USH...                   ← Message Header Extension
    USA...                   ← Acknowledgement Request
    USC...                   ← Unsolicited Commodity Schedule
    BGM+67::9+FP703632526+9' ← Document Type
    DTM+137:20251113:102'    ← Date/Time
    NAD+BY+...               ← Buyer Address
    NAD+SU+...               ← Supplier Address
    UST+01'                  ← Unsolicited Schedule Detail
      LIN+1+...              ← Line Item (Product)
      IMD+...                ← Item Description
      QTY+...                ← Quantity
      DTM+...                ← Delivery Date
    USR+...                  ← Digital Signature
  UNT+14+530266478'          ← Message Trailer
UNZ+1+590880426'             ← Interchange Trailer
```

---

## ✅ Ověření Funkčnosti

### Test 1: Otevření souboru
```pcs
FILEEXIST $0  ; ✓ Ověří existenci EDIFACT souboru
```

### Test 2: Čtení EDIFACT
```pcs
EDIGET @0 $3 "UNB,1,1"  ; ✓ Ověří korektní EDI strukturu
```

### Test 3: XML zápis
```pcs
XMLSAVE @0 $2  ; ✓ Ověří uložení na disk
```

---

## 🛠️ Rozšíření Skriptu

Skript lze snadno rozšířit o:

1. **Více NAD party typů** (Delivery, Invoice, etc.)
2. **ALR segmenty** (Price alerts)
3. **CCI segmenty** (Component details)
4. **RFF segmenty** (Reference numbers)
5. **Databázi export** místo XML
6. **Transformaci na jiné formáty** (JSON, CSV)

---

## 📚 Reference

- EDIFACT COMDIS Standard: D01B
- UN/EDIFACT Syntax Rules
- EAN.UCC Standard for COMDIS
- PCS Scripting Language Documentation

