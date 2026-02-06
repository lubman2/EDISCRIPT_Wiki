# PCS Syntax Guide - EDI Script Language

## Přehled
PCS (Processing Script) je proprietární skriptovací jazyk používaný v EDI systémech pro zpracování EDIFACT, XML a dalších datových formátů. Soubory mají příponu `.pcs` a `.pcf` (compiled).

---

## 1. ZÁKLADNÍ STRUKTURA

### Akce a Labels
```
ACTION 1                    ; Hlavní akce (vstupní bod skriptu)
LABEL LabelName            ; Definice návěští
GOTO LabelName             ; Skok na návěští
```

**Příklad:**
```
ACTION 1
EDIREAD @0 $2 0
IF F THEN ErrorLabel
END

LABEL ErrorLabel
LET $0="Chyba čtení"
RUNS "log.pcf" 1 5
END
```

---

## 2. PROMĚNNÉ

### Typy proměnných
- `$n` - Řetězce (textové proměnné): `$0`, `$1`, `$2`, atd.
- `#n` - Numerické proměnné: `#1`, `#2`, `#3`, atd.
- `@n` - Objekty/Handle (např. otevřené soubory): `@0`, `@1`, atd.

### Přiřazení hodnot
```
LET $1="Hello World"        ; Přiřazení řetězce
LET #5=100                  ; Přiřazení čísla
LET $2=$1+"_suffix"         ; Concatenace
LET #2=#2+1                 ; Inkrementace
```

### Speciální proměnné
- `$0` - Zpravidla hlavní soubor/zpráva
- `$8` - Cesta k programu (PROGPATH $8)
- `#1` - Číslo triády (procesní index)

---

## 3. PRÁCE SE SOUBORY

### Základní operace
```
PROGPATH $8                 ; Načte cestu ke spuštěnému programu
FILENAME $0 $9              ; Extrahuje jen jméno souboru z cesty
FILECOPY $0 $9 [flag]       ; Kopíruje soubor
                            ; flag: 1=overwrite, 3=error handling
FILEDELETE $1               ; Smaže soubor
FILEEXIST $1                ; Testuje existenci (IF F THEN)
FILEOPEN $1                 ; Otevře soubor pro čtení
FILECLOSE                   ; Zavře otevřený soubor
READLINE $2                 ; Čte řádek z otevřeného souboru
```

**Příklady:**
```
; Kopírování souboru
FILECOPY $0 $9 1            ; Přepíše pokud existuje

; Kontrola existence
FILEEXIST $3
IF F THEN DoesntExist       ; Skočí pokud NEEXISTUJE
```

---

## 4. PRÁCE S EDI DATY

### Čtení EDI dokumentů
```
EDIREAD @0 $2 0             ; Načte EDI soubor z $2 do objektu @0
EDIGET @0 $1 "SEGMENT,field,part"  ; Extrahuje data z EDI
EDISET @0 $value "SEGMENT,field,part"  ; Nastaví hodnotu v EDI
EDIWRITE @0 $filename format  ; Zapíše EDI do souboru
EDIMESSAGE @0 #index        ; Selektuje zprávu z interchange
EDIFATHER @0 "SEGMENT,path"  ; Nastaví rodičovský segment
```

**Formát EDIGET/EDISET:**
```
EDIGET @0 $var "SEGMENT,index,subindex,...,qualifier"
EDISET @0 $value "SEGMENT,index,subindex,...,qualifier"

Příklady:
EDIGET @0 $1 "BGM,2,1"      ; Segment BGM, 2. pole, 1. složka
EDIGET @0 $1 "NAD,2,1,,,,1,1,DP"  ; NAD s kvalifikátorem DP
EDIGET @0 $1 "LIN,1,1,,,#2"  ; LIN s číslovanou iterací (#2)
EDIGET @0 $4 "RFF,1,2,,1,,1,1,VA"  ; RFF s kvalifikátorem VA

; Nastavení hodnot:
EDISET @0 $2 "UNB,3,1,,,,3,2,14"  ; Nastaví pole v UNB
EDISET @0 "Test_Value" "FTX,4,1,,1"  ; Nastaví text
```

### XML práce
```
XMLREAD $2 @0               ; Čte XML soubor
XMLTAG @0 "TagName,level"   ; Přistupuje ke XML tagům
XMLTAG @0 "Tag,level,#index" ; S iterací přes více tagů
XMLSAVE @0 "filename"       ; Uloží XML
```

**Příklady XMLTAG:**
```
XMLTAG @0 "VendorForecast,0"  ; Kořenový tag
XMLTAG @0 "Header,1"          ; Tag na úrovni 1
XMLTAG @0 "ItemData,2,#4"     ; Iterace přes více ItemData
XMLTAG @0 "ScheduleLines,3,#5"  ; Vnořené iterace
```

---

## 5. ŘÍDÍCÍ PŘÍKAZY

### Podmínky
```
IF condition THEN label     ; Podmíněný skok
IFFULL $1 THEN label        ; Skočí pokud je proměnná PLNÁ
IFEMPTY $1 THEN label       ; Skočí pokud je proměnná PRÁZDNÁ
IF F THEN label             ; Skočí pokud poslední příkaz SELHAL
IF !F THEN label            ; Skočí pokud poslední příkaz USPĚL
```

**Příklady podmínek:**
```
IF F THEN ErrorHandler              ; Selhání čtení
IFFULL $1 THEN ProcessData          ; Data jsou přítomna
IFEMPTY $1 THEN SkipSection         ; Prázdné pole = přeskočit
IF $1="TEST" THEN HandleTest        ; Porovnání řetězců
IF #1>5 THEN LoopEnd                ; Numerické porovnání
IF $3!="SK" THEN NoSlovakia         ; Negace
IF ~0!=0 THEN End                   ; Porovnání bitů/čísel
```

### Smyčky
```
LABEL LoopStart
...
LET #2=#2+1
IF #2<=10 THEN LoopStart    ; Pokud #2 <= 10, vrátí se na LoopStart
GOTO LoopStart              ; Bezpodmínečný skok
```

### Konfigurační soubory
```
INIREAD $inifile "section" "key" $var
                            ; Čte hodnotu z INI souboru
INIWRITE $inifile "section" "key" $value
                            ; Zapíše hodnotu do INI souboru
```

**Příklady:**
```
LET $9=$8+"edi.ini"
INIREAD $9 "EDI" "Password" $0  ; Čte heslo z konfigurace
```

---

## 6. TEXTOVÉ OPERACE

### Manipulace s řetězci
```
GETTEXT $source $dest start_pos length
                            ; Extrahuje podřetězec
STRCOPY $dest $source pos1 pos2 offset
                            ; Kopíruje část řetězce
STRFIND $string #position "text"
                            ; Hledá pozici textu
STRTOTIME $string #time format
                            ; Konvertuje řetězec na čas
TIMETOSTR #time $string format
                            ; Konvertuje čas na řetězec
```

**Příklady:**
```
GETTEXT $1 $4 1 8           ; Vezme 8 znaků od pozice 1
STRTOTIME $4 #5 2           ; Konvertuje na čas (formát 2)
TIMETOSTR #5 $1 2-          ; Konvertuje čas zpět
STRFIND $1 "'" #5           ; Hledá apostrof
```

---

## 7. PSANÍ A VÝSTUP

### Zápis do souborů
```
WRITE $filename $text       ; Přepíše soubor
WRITEN $filename $text      ; Přidá řádek do souboru
```

**Příklady:**
```
LET $2="BEGIN TRANSACTION"
WRITEN $3 $2                ; Přidá řádek do SQL skriptu

LET $1="Test"
WRITE $1 $2                 ; Vytvoří nový soubor
```

### Spuštění externích příkazů
```
RUNX $command               ; Spustí příkaz (shell)
RUNS $scriptfile params     ; Spustí jiný PCS skript
RUN $command                ; Spustí příkaz
```

**Příklady:**
```
LET $1="CrlfDel.exe "+$0
RUNX $1                     ; Spustí externí program

RUNS "log.pcf" 1 5          ; Spustí log.pcf s parametry
```

---

## 8. PROCEDURY

### Definice a volání procedur
```
PROC ProcedureName          ; Definice procedury
...
RETURN                      ; Návrat z procedury

CALL ProcedureName          ; Volání procedury
```

**Příklad:**
```
PROC DateConv               ; Konvertuje datum
GETTEXT $1 $4 1 8
STRTOTIME $4 #5 2
TIMETOSTR #5 $1 2-
RETURN

; Využití:
EDIGET @0 $1 "DTM,1,2,,,,1,1,137"
CALL DateConv               ; Zavolá proceduru
```

---

## 9. FUNKCE PRO PRÁCI S ČASY

```
GETTEXT $string $dest start length
                            ; Extrahuje znaky
STRTOTIME $string #number format
                            ; Řetězec na čas
TIMETOSTR #number $string format
                            ; Čas na řetězec
```

**Formáty času:**
- `2` - YYYYMMDD (8 znaků)
- `24` - Jiný formát
- `2-` - YYYY-MM-DD
- `24:` - Formát s časem

---

## 10. PRAKTICKÉ PŘÍKLADY

### Příklad 1: Kopírování s kontrolou chyby
```
ACTION 1
PROGPATH $8
FILENAME $0 $9
LET $9=$8+"BACKUP\"+$9
FILECOPY $0 $9 1
IF F THEN ErrorHandler

END

LABEL ErrorHandler
LET $0="Chyba kopírování"
RUNS "log.pcf" 1 5
END
```

### Příklad 2: Čtení a zpracování EDI
```
ACTION 1
EDIREAD @0 "input.edi" 0
IF F THEN ReadError

LET #2=-1
LABEL ProcessLoop
LET #2=#2+1
EDIGET @0 $1 "LIN,1,1,,,#2"
IFEMPTY $1 THEN Finish

; Zpracuj řádek
LET $3="Zpracovávám: "+$1

GOTO ProcessLoop

LABEL Finish
END

LABEL ReadError
LET $0="Chyba čtení EDI"
RUNS "log.pcf" 1 5
END
```

### Příklad 3: Generování SQL
```
ACTION 1
PROGPATH $8
LET $3=$8+"output.sql"
FILEDELETE $3

LET $2="BEGIN TRANSACTION"
WRITEN $3 $2

LET $2="INSERT INTO table VALUES (...)"
WRITEN $3 $2

LET $2="COMMIT TRANSACTION"
WRITEN $3 $2

END
```

### Příklad 4: Manipulace řetězců
```
ACTION 1
LET $1="2020-03-24"

; Odebere pomlčky
GETTEXT $1 $4 1 4           ; Rok
GETTEXT $1 $5 6 2           ; Měsíc
GETTEXT $1 $6 9 2           ; Den
LET $7=$4+$5+$6             ; "20200324"

END
```

---

## 11. STAVOVÉ KÓDY A CHYBY

### Stavová slova
- `F` - False/Failure (poslední příkaz selhal)
- `T` - True (poslední příkaz uspěl)
- `END` - Konec akce
- `RETURN` - Návrat z procedury

### Typické chyby
```
IF F THEN ErrorLabel        ; Řeší selhání
FILEEXIST $1
IF F THEN Doesnt_Exist      ; Soubor neexistuje

EDIREAD @0 $2 0
IF F THEN Read_Error        ; Chyba čtení EDI
```

---

## 15. TISK A GRAFIKA (pro .emf výstupy)

### Nastavení tisku
```
TEXTALIGN alignment         ; Zarovnání textu: LEFT, RIGHT, CENTER
FONT "FontName",size,bold,italic
                            ; Nastavení fontu
```

### Kreslení
```
LINE x1 y1 x2 y2           ; Nakreslí čáru
TEXT x y "text"            ; Umístí text
RECT x1 y1 x2 y2           ; Nakreslí obdélník
CIRCLE x y radius          ; Nakreslí kruh
```

**Příklady:**
```
TEXTALIGN LEFT
FONT "Arial CE",100,,7      ; Arial, velikost 100, bez tučně, bez kurzívy
TEXT 700 20 "Vrácenka"
LINE 30 400 1930 400        ; Vodorovná čára
```

### Výstupní formáty
- `.emf` - Enhanced Metafile (grafický formát pro tisk)
- `.pcs` - Script soubor
- `.pcf` - Compiled script
- `.def` - Definition soubor

---

## 16. POKROČILÉ OPERACE S EDIM

### Modifikace EDI struktur
```
EDISET @0 $value "path"    ; Nastaví hodnotu na cestu
EDIFATHER @0 "path"        ; Nastaví rodičovský segment (umístění)
EDIWRITE @0 $file format   ; Zapíše EDI do souboru
```

**Příklady s EDIFATHER:**
```
; Umístění segmentu pod specifický rodič
EDIFATHER @0 "NAD,1,1,,,,1,1,SU"  ; Umístí data pod NAD SU
EDISET @0 "Praha 10" "NAD,6,1,,,,1,1,SU"
```

### Iterace přes zprávy
```
EDIMESSAGE @0 #2            ; Selektuje zprávu číslo #2
IF F THEN ExitLoop          ; Žádná další zpráva
```

---

## 17. SPECIÁLNÍ DATOVÉ TYPY

### Bitové operace
```
LET ~0=$1                   ; Konvertuje na bitový formát
IF ~0!=0 THEN ...           ; Testuje bitové hodnoty
```

### Časové operace
```
GETTEXT $string $dest start length
STRTOTIME $string #time format  ; Řetězec → čas
TIMETOSTR #time $string format  ; Čas → řetězec
```

---

### Numerované iterace
```
EDIGET @0 $1 "LIN,1,1,,,#2"
; #2 je počítadlo pro iteraci přes více LIN segmentů
```

### Kvalifikátory
```
EDIGET @0 $1 "NAD,2,1,,,,1,1,DP"
; DP = Delivery Party (kvalifikátor)
; Další: SU, SE, BY, UC, IV, VA, ON, atd.
```

### Hierarchie EDI
```
"SEGMENT,field,subfield,element,subelement,occurrence,sequence,qualifier"

Příklad: "NAD,2,1,,,,1,1,DP"
- NAD = segment
- 2 = pole
- 1 = složka
- (prázdné) = element
- (prázdné) = subelement  
- 1 = výskyt
- 1 = sekvence
- DP = kvalifikátor
```

---

## 13. UŽITEČNÉ POZNÁMKY

### Komentáře
```
; Začíná středníkem
; Lze na libovolném místě v řádku
```

### Chování
- Příkazy nejsou case-sensitive
- Řetězce se uzavírají do uvozovek `""`
- Čísla nejsou označena speciálně
- Objekty (@) se používají pro soubory a ED dokumenty

### Běžné chyby
```
; ✓ Správně
LET $1="test"
EDIGET @0 $2 "BGM,2,1"

; ✗ Chyba - chybí uvozovky
LET $1=test

; ✗ Chyba - špatná proměnná
LET @1="text"  ; @ je pro objekty, ne pro řetězce
```

---

## 14. CENÍKY PŘÍKAZŮ

### Primární příkazy
```
ACTION, LABEL, GOTO
LET, IF, IFEMPTY, IFFULL
PROGPATH, FILENAME, FILECOPY, FILEDELETE, FILEEXIST
FILEOPEN, FILECLOSE, READLINE
EDIREAD, EDIGET, EDISET, EDIWRITE, EDIMESSAGE, EDIFATHER
XMLREAD, XMLTAG, XMLSAVE
INIREAD, INIWRITE
WRITE, WRITEN
RUNX, RUNS, RUN
PROC, CALL, RETURN
GETTEXT, STRCOPY, STRFIND
STRTOTIME, TIMETOSTR
TEXTALIGN, FONT, TEXT, LINE, RECT, CIRCLE
END
```

---

## Zdroje v Workspace
- `ORDERS_E2S_WEBEDI.pcs` - Zpracování objednávek do databáze
- `ALL_REMOVE_CRLF.pcs` - Jednoduché spuštění externího programu
- `INTERCHANGE.pcs` - Kopírování souborů
- `INVOIC_FAST_HELP.pcs` - Příklady EDISET, EDIFATHER, EDIWRITE, EDIMESSAGE
- `DELFOR_X2IDOC_MO_LEGO.pcs` - Pokročilé XMLTAG s iteracemi
- `ORDRSP_X2E_D01B.PCS` - Komplexní XML zpracování s EDISET
- `RETANNt.pcs` - Grafika a tisk (TEXTALIGN, FONT, TEXT, LINE)
- `invoic_I2E_D01B_marimex.pcs` - Více ACTION bloků, INIREAD
- `EdiScrpt.chm` - Originální Windows Help soubor (nedostupný v textové formě)

## Poznámka
Tato dokumentace byla vypracována analýzou skriptů ve workspace. Poskytuje praktický přehled syntaxe PCS jazyka s reálnými příklady z používaných skriptů.
