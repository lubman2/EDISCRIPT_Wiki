# EDISCRIPT Wiki - Úplná Dokumentace

Tento projekt obsahuje kompletní dokumentaci, help soubory a konfigurace pro **EDISCRIPT** jazyk (PCS - EDI Processing Control Script) používaný v prostředí **EDICOM**.

---

## 📁 Struktura Projektu

```
EDISCRIPT_Wiki/
├── README.md                          ← Tento soubor
├── Documentation/                     ← Markdown dokumentace
├── HelpFiles/                         ← Původní CHM help soubory z EDICOM
└── VScodeSetup/                       ← VS Code konfigurace pro syntax highlighting
```

---

## 📚 Obsah

### 1. **Documentation/** - Markdown Průvodce
Kompletní technická dokumentace v markdown formátu:

- **PCS_SYNTAX_GUIDE.md** - Úvod do syntaxe EDISCRIPT
- **PCS_OPERACE_REFERENCNI_PRUVODCE.md** - Detailní reference všech operací
- **COMDIS_KOMPLETNI_PRUVODCE.md** - Průvodce projektem COMDIS
- **COMDIS_E2X_MODELCH_DOKUMENTACE.md** - COMDIS EDIFACT→XML konverze
- **COMDIS_VIZUALNI_PREHLED.md** - Vizuální přehled COMDIS struktury
- **COMDIS_XML_SCHEMAT.md** - XML schéma COMDIS
- **README_COMDIS_PROJECT.md** - Informace o COMDIS projektu
- **README_WORKSPACE.md** - Konfigurace workspace

### 2. **HelpFiles/** - EDICOM Help Soubory (.CHM)
Originální help dokumentace z EDICOM prostředí:

- **EdiScrpt.chm** ⭐ - *Hlavní EDISCRIPT dokumentace*
- **EdiScriptEditor.chm** - Help editor EDISCRIPT
- **EdiServer.chm** - EDICOM Server dokumentace
- **EDIExplorer.chm** - EDI Explorator dokumentace
- **Mapper.chm** - Mapper dokumentace
- **emfCreat.chm** - EMF Creator dokumentace
- **logView.chm** - Log Viewer dokumentace
- **ediutil.chm** - EDI Utilities dokumentace

### 3. **VScodeSetup/** - VS Code Konfigurace
Exporty pro barevné zvýraznění v VS Code:

- **pcs.tmLanguage.json.export** - TextMate grammar pro PCS
- **settings.json.export** - Barvy a nastavení pro VS Code
- **PCS_SYNTAX_EXPORT.md** - Instrukce pro import

---

## 🚀 Jak Používat Tuto Dokumentaci

### Pro Studium EDISCRIPT:
1. Začněte s **Documentation/PCS_SYNTAX_GUIDE.md**
2. Pokročilé detaily najdete v **PCS_OPERACE_REFERENCNI_PRUVODCE.md**
3. Pro konkrétní projekty: **COMDIS_KOMPLETNI_PRUVODCE.md**

### Pro Setup VS Code:
1. Jděte do složky **VScodeSetup/**
2. Přečtěte si **PCS_SYNTAX_EXPORT.md**
3. Zkopírujte nastavení do své instance VS Code

### Pro Detailní Help:
- Otevřete příslušný **.chm** soubor z **HelpFiles/**
- Na macOS: Přetáhněte do prohlížeče

---

## 📖 Klíčová Témata

### Základní Operace EDISCRIPT
- **Práce se soubory**: FILECOPY, FILEDELETE, FILEEXIST, FILEOPEN...
- **EDI operace**: EDIREAD, EDIGET, EDISET, EDIWRITE, EDIMESSAGE...
- **XML operace**: XMLREAD, XMLTAG, XMLSAVE, XMLGET, XMLSET...
- **Řetězce**: STRLEN, STRCAT, STRTRIM, STRUPPER, STRLOWER...
- **Proměnné**: $0-$9 (string), #0-#9 (numeric), @0-@9 (object), ~0-~9 (bits)

### Řídící Tokeny
- **IF/THEN/ELSE/ENDIF** - Podmínkové větvení
- **ACTION/PROC** - Definice akcí a procedur
- **LABEL/GOTO** - Skokování
- **RUN/RUNS/RUNX** - Spuštění externích aplikací

---

## 🎨 Barevné Zvýraznění

Projekt obsahuje kompletní nastavení pro VS Code s barvami:
- **Dark Mode**: Optimalizované pro tmavé prostředí
- **Light Mode**: Optimalizované pro světlé prostředí
- Rozlišování: komentáře, řetězce, proměnné, klíčová slova, funkce

---

## 📝 Soubory Projektu

| Složka | Obsah | Formát |
|--------|-------|--------|
| Documentation | Technická průvodce a reference | Markdown (.md) |
| HelpFiles | EDICOM help a dokumentace | CHM Help |
| VScodeSetup | Konfigurace editoru | JSON exports |

---

## ✨ Informace o Projektu

- **Jazyk**: EDISCRIPT (PCS)
- **Prostředí**: EDICOM
- **Zaměření**: EDI transformace (EDIFACT↔XML, databáze, soubory)
- **Primární Projekt**: COMDIS (Sales Forecast EDIFACT→XML)
- **Vytvoření**: 2025-2026

---

## 🔗 Reference

- EDICOM Help: Viz složka **HelpFiles/**
- VS Code Setup: Viz složka **VScodeSetup/**
- Dokumentace: Viz složka **Documentation/**

---

**Poslední aktualizace**: 6. února 2026
