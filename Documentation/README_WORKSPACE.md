# EDICOMRP - EDI Processing Workspace

Komplexní workspace pro zpracování EDI (EDIFACT) zpráv s podporou syntaxe jazyka PCS.

## 📂 Struktura

```
EDICOMRP/
├── .vscode/                          # VS Code konfigurace
│   ├── pcs.tmLanguage.json          # Grammar definice (syntax highlighting)
│   ├── settings.json                # VS Code nastavení
│   ├── language-configuration.json  # Jazykové konfigurace
│   ├── package.json                 # Extension manifest
│   ├── snippets/pcs.json            # Code snippety
│   └── README.md                    # Instalační návod
│
├── PCS_SYNTAX_GUIDE.md              # Kompletní dokumentace PCS jazyka
│
├── *.pcs, *.pcf                     # Processing scripts (EDI)
├── *.def                            # Definition files (EDI formáty)
├── *.emf                            # Enhanced Metafile (tisk/grafika)
├── *.dbf, *.idx                     # Database files
│
└── [pomocné složky]
    ├── INBOX/, OUTBOX/
    ├── ERROR/, ARCHIVE/
    └── ...
```

## 🎨 PCS Syntax Highlighting v VS Code

Workspace je automaticky nakonfigurován pro správné zvýraznění PCS souborů:

- ✅ Barevné zvýraznění všech klíčových prvků
- ✅ Automatické vkládání šablon (snippety)
- ✅ Správná indentace a závorky
- ✅ Komentáře, řetězce a čísla

### Barvy v Dark Mode

| Element | Barva | Příklad |
|---------|-------|---------|
| Klíčová slova | 🔵 Modrá | `ACTION`, `LABEL`, `IF` |
| Proměnné $n | 🔷 Světle modrá | `$0`, `$1`, `$2` |
| Proměnné #n | 🟢 Světle zelená | `#1`, `#2`, `#3` |
| Proměnné @n | 🟦 Tyrkysová | `@0`, `@1` |
| Komentáře | 🟢 Zelená | `; Komentář` |
| Řetězce | 🟠 Oranžová | `"text"` |
| Čísla | 🟢 Světle zelená | `100`, `0`, `5` |
| EDI příkazy | 🟢 Zelená | `EDIREAD`, `EDIGET`, `EDISET` |
| Soubory | 🟨 Žlutá | `FILECOPY`, `FILEEXIST` |
| XML | ⭐ Zlatá | `XMLTAG`, `XMLSAVE` |

## 📝 Quick Start

### 1. Otevřít existující PCS soubor

```bash
code ORDERS_E2S_WEBEDI.pcs
```

Soubor se otevře se správným barevným zvýrazněním.

### 2. Vytvořit nový PCS skript

```bash
touch myScript.pcs
code myScript.pcs
```

### 3. Použít snippety

Např. napsat `action` a stisknout `Tab`:

```pcs
ACTION 1
[kurzor zde]
END
```

### 4. Další snippety

- `proc` → PROCEDURE block
- `if` → IF statement
- `ediread` → EDIREAD statement
- `filecopy` → FILECOPY statement
- `loop` → LOOP block
- ...a více

## 📖 Dokumentace

### 🔍 Syntaxe PCS
Viz [PCS_SYNTAX_GUIDE.md](PCS_SYNTAX_GUIDE.md) pro:
- Úplný přehled příkazů
- Příklady kódu
- Best practices
- Chybové stavy

### 📚 Příklady v workspace

| Soubor | Obsah |
|--------|-------|
| `ORDERS_E2S_WEBEDI.pcs` | Zpracování objednávek do DB |
| `INVOIC_FAST_HELP.pcs` | EDISET, EDIFATHER, EDIWRITE |
| `DELFOR_X2IDOC_MO_LEGO.pcs` | Pokročilé XMLTAG s iteracemi |
| `RETANNt.pcs` | Grafika a tisk |
| `ALL_REMOVE_CRLF.pcs` | Jednoduché spuštění externího programu |

## 🔧 Konfigurace VS Code

Workspace nastavení jsou v `.vscode/settings.json`:

```json
{
  "[pcs]": {
    "editor.tabSize": 2,
    "editor.insertSpaces": true
  },
  "files.associations": {
    "*.pcs": "pcs",
    "*.pcf": "pcs"
  }
}
```

## 🎯 Podporované příkazy

### Řídící prvky
```pcs
ACTION 1           ; Akce vstupní bod
LABEL name         ; Návěští
GOTO name          ; Skok na návěští
PROC ProcName      ; Definice procedury
CALL ProcName      ; Volání procedury
RETURN             ; Návrat z procedury
```

### Podmínky
```pcs
IF $1="test" THEN label      ; Podmíněný skok
IFFULL $1 THEN label         ; Pokud PLNÝ
IFEMPTY $1 THEN label        ; Pokud PRÁZDNÝ
IF F THEN ErrorHandler       ; Pokud SELHALO
```

### EDI
```pcs
EDIREAD @0 $2 0              ; Čte EDI
EDIGET @0 $1 "BGM,2,1"       ; Extrahuje data
EDISET @0 $value "BGM,2,1"   ; Nastaví data
EDIWRITE @0 $file 2          ; Zapíše EDI
```

### Soubory
```pcs
FILECOPY $src $dst 1         ; Kopíruje soubor
FILEDELETE $file             ; Smaže soubor
FILEEXIST $file              ; Testuje existenci
READLINE $var                ; Čte řádek
```

### XML
```pcs
XMLREAD $file @0             ; Čte XML
XMLTAG @0 "Tag,level"        ; Přistupuje tagu
XMLSAVE @0 $file             ; Uloží XML
```

## 🐛 Řešení problémů

### Zvýraznění se neaplikuje

1. Restartujte VS Code
   ```
   Cmd/Ctrl + Shift + P → Reload Window
   ```

2. Zkontrolujte nastavení souboru
   ```
   Cmd/Ctrl + Shift + P → Change Language Mode → PCS
   ```

### Snippety nefungují

1. Ujistěte se, že je soubor `.pcs` asociován
   ```json
   "files.associations": {
     "*.pcs": "pcs"
   }
   ```

2. Restartujte VS Code

## 📊 Statistiky

- **Celkem PCS skriptů**: ~450+ souborů
- **Klíčových slov**: 50+
- **Podporovaných formátů**: EDIFACT, XML, IDOC, VDA, SQL
- **Procedur**: Vlastní procedury s PROC/CALL

## 🔗 Soubory

- `.pcs` - Processing Script
- `.pcf` - Processed/Compiled File
- `.def` - Definition file
- `.emf` - Enhanced Metafile (tisk)
- `.dbf` / `.idx` - Database files

## 📝 Poznámky

- PCS je proprietární jazyk EDI systému Edicomrp
- Syntax je case-insensitive
- Komentáře začínají `;`
- Řetězce se uzavírají do `"`
- Proměnné: `$` (text), `#` (čísla), `@` (objekty), `~` (bity)

---

**Workspace**: EDICOMRP  
**Datum vytvoření**: 23. ledna 2026  
**Jazyk**: PCS (EDI Script Language)  
**VS Code verze**: 1.50+
