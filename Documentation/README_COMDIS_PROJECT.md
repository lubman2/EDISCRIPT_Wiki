# 🎯 COMDIS EDIFACT → XML Converter - README

## 📋 Obsah Projektu

Tento projekt obsahuje kompletní řešení pro konverzi EDIFACT COMDIS zpráv do strukturovaného XML formátu.

---

## 📦 Soubory v Projektu

### 🔴 Hlavní Skript
- **`COMDIS_E2X_MODELCH.pcs`** - PCS skript pro konverzi
  - Zdrojový kód (interpretován pomocí EDIScrpt.exe)
  - Po kompilaci se stane `COMDIS_E2X_MODELCH.pcf`
  - Čte EDIFACT → vytváří XML → ukládá na disk

### 📚 Dokumentace (Markdown)

1. **`COMDIS_KOMPLETNI_PRUVODCE.md`** 📖
   - ⭐ **ZAČNĚTE TADY** - Komplexní průvodce
   - EDIFACT struktura COMDIS
   - Cílový XML formát
   - Kroky k realizaci
   - Příklady mapování

2. **`COMDIS_E2X_MODELCH_DOKUMENTACE.md`** 🔍
   - Detailní dokumentace skriptu
   - Mapovací tabulka EDIFACT → XML
   - Popis každé PCS operace
   - Příklady použití

3. **`COMDIS_XML_SCHEMAT.md`** 🏗️
   - Vizuální stromová struktura XML
   - XSD schéma definice
   - Transformační diagram
   - Příklady výstupního XML

4. **`PCS_OPERACE_REFERENCNI_PRUVODCE.md`** 📖
   - Kompletní reference všech PCS operací
   - XML operace (XMLCREATE, XMLTAG, XMLSAVE...)
   - EDIFACT operace (EDIREAD, EDIGET, EDISET...)
   - Stringové a řídící operace
   - Příklady kódu

5. **`COMDIS_VIZUALNI_PREHLED.md`** 📊
   - Vizuální diagramy a přehledy
   - Architektura řešení
   - Tok dat diagramy
   - Tabulky segmentů

---

## 🚀 Jak Začít?

### Krok 1: Pochopení Struktury
```
1. Přečtěte si: COMDIS_KOMPLETNI_PRUVODCE.md
   └─ Pochopíte co skript dělá a proč
```

### Krok 2: Implementace (Windows)
```
1. Zkopírujte COMDIS_E2X_MODELCH.pcs na Windows
2. Otevřete EDIScrpt.exe
3. Otevřete soubor a zkompilujte
4. Výsledek: COMDIS_E2X_MODELCH.pcf
```

### Krok 3: Testování
```bash
# Spusťte skript s testovacím EDIFACT souborem:
ProcRun.exe -a1 -fCOMDIS_E2X_MODELCH.pcf -$0="comdis_test.edi"

# Ověřte výstupní XML:
OUTPUT/COMDIS_comdis_test.xml
```

### Krok 4: Integracija
```
Přidejte do svého automatizačního skriptu (Receive_ALL.cmd)
```

---

## 🎯 Co Skript Dělá?

```
VSTUP: EDIFACT COMDIS soubor
  ↓
ČTENÍ: Parsuje EDIFACT segmenty
  - UNB (Interchange Header)
  - UNH (Message Header)
  - NAD (Party Information)
  - USC/LIN (Forecast Periods & Items)
  ↓
TRANSFORMACE: Konvertuje do XML
  - Vytváří hierarchickou strukturu
  - Mapuje segmenty na XML elementy
  - Zpracovává smyčky (periody, položky)
  ↓
VÝSTUP: Strukturovaný XML soubor
  - Uloží do OUTPUT/ adresáře
  - Jméno: COMDIS_<vstupní_jméno>.xml
```

---

## 📊 XML Výstupní Struktura

```xml
<COMDIS>
  ├─ <Header>              ← Metadata zprávy
  │  ├─ Interchange        ← UNB data
  │  ├─ Message            ← UNH data
  │  ├─ MessageMetadata    ← USH data
  │  └─ DocumentInfo       ← BGM+DTM data
  │
  ├─ <Parties>             ← Obchodní partneři
  │  ├─ Buyer              ← NAD+BY
  │  └─ Supplier           ← NAD+SU
  │
  ├─ <ForecastPeriods>     ← Prognózní data
  │  ├─ Period[0]          ← USC perioda
  │  │  └─ Items           ← Produkty
  │  │     ├─ Item[0]      ← LIN + IMD + QTY
  │  │     └─ Item[1]
  │  └─ Period[1]
  │
  └─ <Control>             ← Kontrolní součty
     ├─ SegmentCount       ← CNT
     └─ MessageControlCount ← UNZ
```

---

## 💡 Příklad Transformace

### Vstup (EDIFACT):
```edifact
NAD+BY+8594195490002::9++Smarty CZ a.s.'
NAD+SU+8595149000001::9++AT Computers a.s.'
USC+01643674+++++2+4'
LIN+1+PROD001+++...'
IMD+...+Laptop Model X1'
QTY+1:100:PCE'
```

### Výstup (XML):
```xml
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
        <ProductDescription>Laptop Model X1</ProductDescription>
        <Quantity>100</Quantity>
        <Unit>PCE</Unit>
      </Item>
    </Items>
  </Period>
</ForecastPeriods>
```

---

## 🔧 Technické Detaily

| Vlastnost | Hodnota |
|-----------|---------|
| **Jazyk** | PCS (EDI Script Language) |
| **Kompilátor** | EDIScrpt.exe (Windows) |
| **Spouštěč** | ProcRun.exe (Windows) |
| **Vstup** | EDIFACT COMDIS (D01B) |
| **Výstup** | XML 1.0 UTF-8 |
| **Podporované periody** | 1-999 |
| **Podporované položky** | 1-999 per periodu |
| **Chybový handling** | Via log.pcf |

---

## 🎛️ Klíčové PCS Operace

### XML Práce:
```pcs
XMLCREATE @0              ; Vytvoří nový XML
XMLTAG @0 "Element,1"     ; Navigace/Vytvoření
XMLTEXTSET @0 $text       ; Zápis textu
XMLSAVE @0 $filename      ; Uložení
```

### EDIFACT Práce:
```pcs
EDIREAD @0 $file 0        ; Čtení EDIFACT
EDIGET @0 $var "SEG,1,1"  ; Čtení segmentu
IF F THEN ErrorHandler    ; Error check
```

### Smyčky:
```pcs
LET #1=-1
LABEL NextPeriod
LET #1=#1+1
EDIGET @0 $3 "USC,1,1,,,#1"
IFEMPTY $3 THEN EndPeriods
; ... kód ...
GOTO NextPeriod
LABEL EndPeriods
```

---

## 📂 Doporučená Struktura Složek

```
D:\EDICOMRP\
├── COMDIS_E2X_MODELCH.pcs      ← Váš skript (zdroj)
├── COMDIS_E2X_MODELCH.pcf      ← Kompilovaná verze
├── INBOX/                       ← Vstupní EDIFACT
│   └── comdis_001.edi
├── OUTPUT/                      ← Výstupní XML
│   └── COMDIS_comdis_001.xml
├── LOG/                         ← Log soubory
│   └── COMDIS_*.log
└── Dokumentace/
    ├── COMDIS_KOMPLETNI_PRUVODCE.md
    ├── COMDIS_E2X_MODELCH_DOKUMENTACE.md
    ├── COMDIS_XML_SCHEMAT.md
    ├── PCS_OPERACE_REFERENCNI_PRUVODCE.md
    └── COMDIS_VIZUALNI_PREHLED.md
```

---

## 🐛 Řešení Problémů

| Problém | Řešení |
|---------|--------|
| **"Failed to create XML"** | Zkontrolujte práva zápisu na OUTPUT/ |
| **"File not found"** | Ověřte cestu k EDIFACT vstupnímu souboru |
| **"Invalid format"** | Ověřte syntaxi EDIFACT (UNA, UNB, UNH) |
| **Prázdný XML** | Zkontrolujte dostupnost USC/LIN segmentů |
| **Chyba kompilace** | Zkontrolujte syntaxi PCS (příkazy, proměnné) |

---

## ✅ Checklist Implementace

- [ ] Přečtěte si COMDIS_KOMPLETNI_PRUVODCE.md
- [ ] Zkopírujte COMDIS_E2X_MODELCH.pcs na Windows
- [ ] Otevřete EDIScrpt.exe a zkompilujte
- [ ] Vytvořte OUTPUT/ složku v EDICOMRP
- [ ] Testujte s vzorkovým EDIFACT COMDIS souborem
- [ ] Ověřte vygenerovaný XML
- [ ] Přidejte do automatizačního skriptu
- [ ] Nastavte logging a alerting
- [ ] Zdokumentujte v soupisu procesů

---

## 📚 Dokumentační Průvodce

```
┌─────────────────────────────────────┐
│ Chci pochopit obecně                │
│ → COMDIS_VIZUALNI_PREHLED.md        │
│   (diagramy a přehledy)             │
└─────────────────────────────────────┘

┌─────────────────────────────────────┐
│ Chci být krok za krokem             │
│ → COMDIS_KOMPLETNI_PRUVODCE.md      │
│   (detailní návod)                  │
└─────────────────────────────────────┘

┌─────────────────────────────────────┐
│ Chci pochopit XML strukturu         │
│ → COMDIS_XML_SCHEMAT.md             │
│   (stromová struktura, XSD)         │
└─────────────────────────────────────┘

┌─────────────────────────────────────┐
│ Chci pochopit PCS skript            │
│ → COMDIS_E2X_MODELCH_DOKUMENTACE.md │
│   (komentáře a vysvětlení)          │
└─────────────────────────────────────┘

┌─────────────────────────────────────┐
│ Chci referenci na PCS operace       │
│ → PCS_OPERACE_REFERENCNI_PRUVODCE.md│
│   (všechny funkce s příklady)       │
└─────────────────────────────────────┘
```

---

## 🔗 Souvztažnost Souborů

```
COMDIS_KOMPLETNI_PRUVODCE.md
    ├─ Odkazuje na: COMDIS_VIZUALNI_PREHLED.md
    ├─ Odkazuje na: COMDIS_XML_SCHEMAT.md
    └─ Odkazuje na: PCS_OPERACE_REFERENCNI_PRUVODCE.md

COMDIS_E2X_MODELCH_DOKUMENTACE.md
    ├─ Odkazuje na: COMDIS_E2X_MODELCH.pcs
    └─ Odkazuje na: PCS_OPERACE_REFERENCNI_PRUVODCE.md

COMDIS_XML_SCHEMAT.md
    └─ Vizuální reprezentace výstupu
```

---

## 📞 Kontakt & Podpora

- **Verze:** 1.0
- **Datum vytvoření:** 23. ledna 2026
- **Status:** Připraveno k implementaci
- **Ověření na:** macOS (vytvořeno), Windows (implementace)

---

## 🎓 Učící Se Zdroje

Pro hlubší porozumění doporučujeme:

1. **EDIFACT:**
   - UN/EDIFACT D01B Specifikace
   - GS1 EAN.UCC COMDIS Příručka

2. **PCS Jazyk:**
   - EdiScrpt.chm (Help soubor)
   - PCS_OPERACE_REFERENCNI_PRUVODCE.md (v tomto projektu)

3. **XML:**
   - W3C XML Specification
   - COMDIS_XML_SCHEMAT.md (XSD v tomto projektu)

---

## 📝 Poznámka o Autorství

Toto řešení bylo vytvořeno na základě:
- Analýzy existujících PCS skriptů v projektu
- Studia EDIFACT COMDIS struktury
- Best practices z podobných EDI transformací

**Skript je modulární a snadno rozšiřitelný** pro nové segmenty nebo transformace.

---

**Dobré štěstí s implementací! 🚀**

