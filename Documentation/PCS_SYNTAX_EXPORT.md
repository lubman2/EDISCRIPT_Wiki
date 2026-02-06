# Export Barevné Syntaxe PCS pro VS Code

Tento export obsahuje kompletní konfiguraci barevného zvýraznění a gramatiky pro soubory `.pcs` a `.pcf`.

## Jak importovat v jiné instanci VS Code:

### 1. Zkopírujte grammar soubor
Zkopírujte soubor `pcs.tmLanguage.json` do:
```
~/.vscode/extensions/pcs-language-<version>/syntaxes/pcs.tmLanguage.json
```

Nebo přidejte do `.vscode/` složky projektu v nové instanci.

### 2. Zkopírujte nastavení
Přidejte obsah z `settings.json.export` do `settings.json` vaší nové instalace.

### 3. Alternativa: VS Code Settings Sync
Použijte VS Code's Settings Sync (Settings > Profiles > Export Profile) pro synchronizaci všech nastavení mezi instancemi.

## Soubory v tomto exportu:

- **pcs.tmLanguage.json** - TextMate grammar definice pro PCS jazyk
- **settings.json.export** - Barvy a konfigurace pro oba světelné režimy (Dark/Light)

---

**Export vytvořen:** 6. února 2026
**Jazyk:** PCS (EDI Script Language)
**Formáty:** .pcs, .pcf
