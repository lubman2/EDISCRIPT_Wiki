# COMDIS Projekt - Vizuální Přehled

## 🎯 Co Jsme Vytvořili

```
┌─────────────────────────────────────────────────────────┐
│                                                         │
│         EDIFACT COMDIS → XML CONVERTER                 │
│                                                         │
│  VSTUP: EDIFACT Message                               │
│  (COMDIS - Sales Forecasting)                          │
│         │                                              │
│         ↓                                              │
│  ┌──────────────────────┐                             │
│  │ COMDIS_E2X_MODELCH   │  PCS Skript                │
│  │ .pcs (zdrojový kód)  │                             │
│  │ .pcf (kompilovaný)   │                             │
│  └──────────────────────┘                             │
│         │                                              │
│         ↓                                              │
│  VÝSTUP: Strukturovaný XML                            │
│  (s Header, Parties, Items, Control)                  │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

---

## 📂 Vytvořené Soubory

```
EDICOMRP/
│
├── COMDIS_E2X_MODELCH.pcs
│   └─ PCS skript pro konverzi EDIFACT → XML
│      • Čte EDIFACT segmenty (UNB, UNH, USC, LIN, NAD...)
│      • Vytváří XML strukturu
│      • Zpracovává smyčky (periody, položky)
│      • Ukládá XML na disk
│
├── COMDIS_E2X_MODELCH_DOKUMENTACE.md
│   └─ Detailní dokumentace skriptu
│      • Struktura XML
│      • Mapování EDIFACT segmentů
│      • Popis PCS operací
│      • Příklady použití
│
├── COMDIS_XML_SCHEMAT.md
│   └─ Vizuální schéma XML
│      • Stromová struktura
│      • XSD definice
│      • EDIFACT → XML příklady
│      • Transformační diagram
│
├── PCS_OPERACE_REFERENCNI_PRUVODCE.md
│   └─ Kompletní reference PCS operací
│      • XML operace (XMLCREATE, XMLTAG, XMLSAVE...)
│      • EDIFACT operace (EDIREAD, EDIGET, EDISET...)
│      • Stringové operace (STRCOPY, STRFIND...)
│      • Řídící operace (IF/THEN, GOTO, CALL...)
│      • Souborové operace (FILEEXIST, FILECOPY...)
│      • Příklady kódu
│
└── COMDIS_KOMPLETNI_PRUVODCE.md
    └─ Komplexní průvodce
       • Přehled řešení
       • EDIFACT struktura
       • Cílový XML formát
       • Jak skript funguje
       • Mapování tabulky
       • Kroky implementace
```

---

## 🏗️ Architektura Řešení

### Vrstva 1: EDIFACT Zpracování
```
┌────────────────────────────────┐
│   EDIFACT COMDIS Soubor        │
│                                │
│  UNB - Interchange Header      │
│  UNH - Message Header          │
│  USH - Message Metadata        │
│  BGR - Document Type           │
│  DTM - Date/Time              │
│  NAD - Name & Address         │
│  USC - Forecast Schedule      │
│  LIN - Line Items             │
│  IMD - Description            │
│  QTY - Quantity               │
│  DTM - Delivery Date          │
│  UNT - Message Trailer        │
│  UNZ - Interchange Trailer    │
│                                │
└────────────────────────────────┘
         │
      EDIREAD
         │
         ↓
```

### Vrstva 2: XML Vytváření
```
┌────────────────────────────────┐
│   XML Objekt (@0)              │
│                                │
│  XMLCREATE - inicializace      │
│  XMLTAG - navigace             │
│  XMLTEXTSET - zápis textu      │
│                                │
└────────────────────────────────┘
         │
      XMLSAVE
         │
         ↓
```

### Vrstva 3: XML Výstup
```
┌────────────────────────────────┐
│   Strukturovaný XML            │
│                                │
│  <COMDIS>                      │
│    <Header>                    │
│    <Parties>                   │
│    <ForecastPeriods>           │
│    <Control>                   │
│  </COMDIS>                     │
│                                │
└────────────────────────────────┘
```

---

## 🔄 Tok Dat

```
EDIFACT Vstup
    │
    ├─→ PROGPATH $8          [Cesta programu]
    ├─→ FILEEXIST $0         [Ověření vstupu]
    └─→ EDIREAD @0 $0 0      [Čtení EDIFACT]
        │
        ├─→ UNB čtení
        │   ├─→ EDIGET "UNB,1,1" → XMLTAG → XMLTEXTSET
        │   ├─→ EDIGET "UNB,2,1" → XMLTAG → XMLTEXTSET
        │   └─→ ... více polí
        │
        ├─→ UNH čtení
        │   ├─→ Message Type
        │   ├─→ Version
        │   └─→ Release
        │
        ├─→ NAD čtení (Parties)
        │   ├─→ BY (Buyer)
        │   └─→ SU (Supplier)
        │
        ├─→ USC SMYČKA (#1)
        │   │
        │   ├─→ PeriodNumber
        │   │
        │   └─→ LIN SMYČKA (#2)
        │       ├─→ LineItemNumber
        │       ├─→ ProductNumber
        │       ├─→ IMD čtení
        │       ├─→ QTY čtení
        │       └─→ DTM čtení
        │
        ├─→ CNT čtení (Control)
        └─→ UNZ čtení
            │
            └─→ XMLSAVE @0 $2
                │
                └─→ XML Výstupní Soubor
```

---

## 📊 Tabulka Segmentů

| Segment | Úroveň | Popis | Frekvence | XML Element |
|---------|--------|-------|-----------|-------------|
| **UNB** | 0 | Interchange Header | 1 | `Interchange` |
| **UNH** | 1 | Message Header | 1 | `Message` |
| **USH** | 1 | Message Metadata | 1 | `MessageMetadata` |
| **USA** | 1 | Acknowledgement Req | 0..1 | - |
| **USC** | 1 | Forecast Schedule | 1..n | `Period` |
| **UST** | 2 | Schedule Detail | 1 | Period props |
| **BGM** | 1 | Document Type | 1 | `DocumentInfo` |
| **DTM** | 1 | Date/Time | 1..n | `CreationDate` |
| **NAD** | 1 | Address | 2..n | `Buyer`, `Supplier` |
| **DOC** | 1 | Reference | 0..1 | - |
| **LIN** | 2 | Line Item | 1..n | `Item` |
| **IMD** | 2 | Item Description | 0..1 | `ProductDescription` |
| **QTY** | 2 | Quantity | 1 | `Quantity`, `Unit` |
| **DTM** | 2 | Delivery Date | 0..1 | `DeliveryDate` |
| **USR** | 1 | Signature | 0..1 | - |
| **UNT** | 1 | Message Trailer | 1 | - |
| **CNT** | 0 | Control Total | 1..n | `Control` |
| **UNZ** | 0 | Interchange Trailer | 1 | - |

---

## 🎛️ PCS Operace v Diagramu

### Čtení → Zápis Tok
```
┌─────────────────────────────┐
│     EDIREAD @0 $file        │ ← Čtení EDIFACT
└──────────────┬──────────────┘
               │
        ┌──────┴──────┐
        │             │
    ┌───▼────┐    ┌──▼──────┐
    │ EDIGET │    │ IF / IF F│  Čtení & Kontrola
    │ $var   │    │ THEN     │
    └───┬────┘    └──┬──────┘
        │            │
        └────┬───────┘
             │
        ┌────▼──────────┐
        │ XMLCREATE @0  │  Inicializace
        └────┬──────────┘
             │
        ┌────▼────────────┐
        │ XMLTAG @0 "..." │  Navigace
        └────┬────────────┘
             │
    ┌────────▼──────────┐
    │ XMLTEXTSET @0 $v  │  Zápis textu
    └────┬──────────────┘
         │
    ┌────▼────────────┐
    │ XMLSAVE @0 $f   │  Uložení
    └────────────────┘
         │
         └─→ XML Soubor
```

---

## 🔗 Vazby Mezi Dokumenty

```
┌─────────────────────────────────────────────────────┐
│                                                     │
│  COMDIS_KOMPLETNI_PRUVODCE.md  ←─────┐            │
│  └─ Rozsáhlý návod                   │            │
│                                      │            │
│  COMDIS_E2X_MODELCH.pcs ←────┐      │            │
│  └─ Vlastní skript             │      │            │
│                                │      │            │
│  COMDIS_E2X_MODELCH_DOKUMENTACE.md  │            │
│  └─ Specifická dokumentace skriptu  │            │
│                                      │            │
│  COMDIS_XML_SCHEMAT.md ←─────────┐  │            │
│  └─ XML struktura a XSD           │  │            │
│                                   │  │            │
│  PCS_OPERACE_REFERENCNI_PRUVODCE  │  │            │
│  └─ Reference všech PCS operací ──┼──┘            │
│                                   │                │
│  Tato dokumentace                 │                │
│  └─ Vizuální přehled             └────────────────┘
│
└─────────────────────────────────────────────────────┘
```

---

## 📈 Příklad Transformace

### EDIFACT Input:
```edifact
UNB+UNOD:3+8594195490002:14+8595149000001:14+251113:2013+590880426+++++EANCOM'
UNH+530266478+COMDIS:D:01B:UN:EAN003'
...
NAD+BY+8594195490002::9++Smarty CZ a.s.'
NAD+SU+8595149000001::9++AT Computers a.s.'
...
USC+01643674+++++2+4'
LIN+1+PROD001+++...'
IMD+...+Laptop Model X1'
QTY+1:100:PCE'
DTM+2:20251120'
...
UNT+14+530266478'
UNZ+1+590880426'
```

### XML Output:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<COMDIS>
  <Header>
    <Interchange>
      <Sender>8594195490002:14</Sender>
      <Receiver>8595149000001:14</Receiver>
    </Interchange>
    <Message>
      <MessageType>COMDIS</MessageType>
      <Version>D</Version>
    </Message>
  </Header>
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
  <ForecastPeriods>
    <Period index="0">
      <PeriodNumber>01643674</PeriodNumber>
      <Items>
        <Item index="0">
          <ProductNumber>PROD001</ProductNumber>
          <Quantity>100</Quantity>
          <Unit>PCE</Unit>
          <DeliveryDate>20251120</DeliveryDate>
        </Item>
      </Items>
    </Period>
  </ForecastPeriods>
  <Control>
    <SegmentCount>14</SegmentCount>
    <MessageControlCount>1</MessageControlCount>
  </Control>
</COMDIS>
```

---

## ✨ Klíčové Vlastnosti

```
╔═══════════════════════════════════════════════════════╗
║                                                       ║
║  ✓ Plná podpora COMDIS EDIFACT (D01B)               ║
║  ✓ Automatická detekce period a položek             ║
║  ✓ Chybový handling a logging                       ║
║  ✓ Bezpečné smyčky (ochrana proti nekonečnu)       ║
║  ✓ Modulární design (snadno rozšiřitelné)           ║
║  ✓ Detailní dokumentace s příklady                  ║
║  ✓ Mapování všech relevantních segmentů             ║
║  ✓ XML validace schématem                           ║
║                                                       ║
╚═══════════════════════════════════════════════════════╝
```

---

## 🚀 Příští Kroky

1. **Na Windows:**
   - Zkompilovat: `EDIScrpt.exe COMDIS_E2X_MODELCH.pcs`
   - Testovat: `ProcRun.exe -a1 -fCOMDIS_E2X_MODELCH.pcf -$0="test.edi"`

2. **Ověřit XML:**
   - Otevřít v XML editoru (VS Code)
   - Validovat proti schématu
   - Testovat transformace

3. **Integrovat:**
   - Přidat do Receive_ALL.cmd
   - Nastavit logování
   - Zprovoznit automatizaci

4. **Rozšířit:**
   - Přidat další segmenty (RFF, AJT...)
   - Filtrování podle kritérií
   - Export do jiných formátů

---

## 📞 Poznámky

**Vytvoření:** 23. ledna 2026
**Verze:** 1.0
**Status:** Připraveno k implementaci
**Testování:** Čeká na Windows prostředí s EDIScrpt.exe

