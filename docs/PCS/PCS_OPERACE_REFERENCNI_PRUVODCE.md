# PCS Skriptovací Operace - Referenční Průvodce

## 📚 Základní Kategorie Operací

---

## 1. 🔧 XML OPERACE

### XMLCREATE - Vytvoření XML dokumentu
```pcs
XMLCREATE @0
```
**Popis:** Vytvoří nový XML dokument v objektu @0  
**Parametry:** @0 = XML objekt  
**Vrací:** F pokud selhá  
**Příklad:**
```pcs
XMLCREATE @0
IF F THEN ErrXmlCreate
```

### XMLOPEN - Otevření XML ze souboru
```pcs
XMLOPEN @0 $filename
```
**Popis:** Načte XML soubor do objektu @0  
**Parametry:** 
- @0 = XML objekt
- $filename = cesta k XML souboru  
**Příklad:**
```pcs
XMLOPEN @0 "source.xml"
IF F THEN ErrOpen
```

### XMLTAG - Navigace/Vytvoření XML elementů
```pcs
XMLTAG @0 "ElementName,level"          ; Vytvoří element
XMLTAG @0 "ElementName,level,index"    ; S indexem
```
**Popis:** Přejde/vytvoří element na dané úrovni  
**Parametry:**
- @0 = XML objekt
- ElementName = jméno elementu
- level = hloubka (0=root, 1=child, 2=grandchild...)
- index = (volitelný) číslovaný index  
**Příklad:**
```pcs
XMLTAG @0 "COMDIS,0"              ; <COMDIS>
XMLTAG @0 "Header,1"              ; <Header>
XMLTAG @0 "Party,2,#1"            ; <Party index="1">
```

### XMLTEXTSET - Vložení textu do elementu
```pcs
XMLTEXTSET @0 $text
```
**Popis:** Vloží text do aktuálního elementu  
**Parametry:**
- @0 = XML objekt
- $text = řetězec k vložení  
**Příklad:**
```pcs
XMLTAG @0 "Name,3"
XMLTEXTSET @0 $3        ; Vloží obsah $3 do <Name>
```

### XMLTEXTGET - Čtení textu z elementu
```pcs
XMLTEXTGET @0 $variable
```
**Popis:** Čte text z aktuálního elementu  
**Parametry:**
- @0 = XML objekt
- $variable = proměnná pro uložení  
**Příklad:**
```pcs
XMLTAG @0 "Name,3"
XMLTEXTGET @0 $3        ; Přečte <Name> do $3
```

### XMLSAVE - Uložení XML do souboru
```pcs
XMLSAVE @0 $filename
```
**Popis:** Uloží XML dokument na disk  
**Parametry:**
- @0 = XML objekt
- $filename = výstupní cesta  
**Příklad:**
```pcs
XMLSAVE @0 "output.xml"
IF F THEN ErrSave
```

---

## 2. 🎯 EDIFACT OPERACE

### EDIREAD - Načtení EDIFACT souboru
```pcs
EDIREAD @0 $filename format
```
**Popis:** Načte EDIFACT soubor do objektu  
**Parametry:**
- @0 = EDI objekt
- $filename = cesta
- format = 0 (EDIFACT) / 1 (X12) / 2 (XML)  
**Příklad:**
```pcs
EDIREAD @0 $0 0
IF F THEN ErrRead
```

### EDIGET - Čtení EDIFACT segmentu
```pcs
EDIGET @0 $variable "SEGMENT,pos1,pos2"
EDIGET @0 $variable "SEGMENT,pos1,pos2,,#loop"
```
**Popis:** Extrahuje data ze segmentu EDIFACT  
**Parametry:**
- SEGMENT = čtyřznakový kód (UNB, NAD, LIN...)
- pos1,pos2 = pozice v segmentu
- #loop = (volitelný) počítadlo smyčky  
**Vrací:** F pokud segment neexistuje  

**Příklady:**
```pcs
; Čtení UNB - Sender
EDIGET @0 $3 "UNB,2,1"
; Čtení NAD (n-tý výskyt)
EDIGET @0 $3 "NAD,2,2"
; Čtení LIN se smyčkou
EDIGET @0 $3 "LIN,1,1,,1,#2,,,#1"
```

### EDISET - Zápis do EDIFACT segmentu
```pcs
EDISET @0 $text "SEGMENT,pos1,pos2"
```
**Popis:** Zapíše/změní hodnotu v segmentu  
**Parametry:** Stejné jako EDIGET  
**Příklad:**
```pcs
EDISET @0 "TEST" "BGM,1,1"        ; Změní BGM,1,1 na "TEST"
```

### EDIWRITE - Zápis EDIFACT do souboru
```pcs
EDIWRITE @0 $filename format
```
**Popis:** Uloží EDIFACT (posíleně/upravený) na disk  
**Parametry:**
- @0 = EDI objekt
- $filename = výstupní cesta
- format = 0/1/2 (EDIFACT/X12/XML)  
**Příklad:**
```pcs
EDIWRITE @0 "output.edi" 0
```

### EDICOUNT - Počet segmentů
```pcs
EDICOUNT @0 #number
```
**Popis:** Vrátí počet nějakého segmentu  
**Příklad:**
```pcs
EDICOUNT @0 #4
LET #4=#4-1
```

---

## 3. 📝 STRINGOVÉ OPERACE

### STRCOPY - Kopírování podřetězce
```pcs
STRCOPY $source $dest start_pos length target_pos
```
**Popis:** Kopíruje část řetězce  
**Parametry:**
- $source = zdrojový řetězec
- $dest = cílová proměnná
- start_pos = kde začít (1-based)
- length = kolik znaků
- target_pos = kam v cíli  
**Příklad:**
```pcs
STRCOPY "ABCDEFGH" $0 2 3 1    ; $0 = "BCD"
```

### STRFIND - Hledání v řetězci
```pcs
STRFIND $text $substring #position
```
**Popis:** Najde pozici podřetězce  
**Vrací:** Pozici nebo -1 pokud nenajde  
**Příklad:**
```pcs
STRFIND $0 "/" #2
IF #2=-1 THEN NotFound
```

### STRLEN - Délka řetězce
```pcs
STRLEN $text #length
```

### STRTOTIME - Konverze řetězce na čas
```pcs
STRTOTIME $date #time format
```
**Příklad:**
```pcs
STRTOTIME "20251113" #2 2       ; format: 2=YYMMDD
```

### TIMETOSTR - Konverze času na řetězec
```pcs
TIMETOSTR #time $date format
```

---

## 4. 🔢 NUMERICKÉ OPERACE

### LET - Přiřazení hodnoty
```pcs
LET $variable="text"            ; String
LET #variable=100               ; Numeric
LET @variable=object            ; Object
LET ~variable=1                 ; Bit
```

### Matematické operace
```pcs
LET #1=#1+1                     ; Inkrementace
LET #2=#1*2                     ; Násobení
LET #3=#1-5                     ; Odčítání
```

---

## 5. 🎮 ŘÍDÍCÍ OPERACE

### IF/THEN/ELSE - Podmínka
```pcs
IF condition THEN label1
IF condition THEN label1 ELSE label2
```

**Podmínky:**
- `F` = File/Operation failed
- `!F` = File/Operation succeeded
- `#1=-1` = Numeric comparison
- `$1="text"` = String comparison
- `IFEMPTY $1 THEN label` = Prázdný řetězec

**Příklady:**
```pcs
IF F THEN ErrorHandler           ; Pokud selhalo čtení
IF !F THEN Success               ; Pokud uspělo
IF $3="EMPTY" THEN SkipItem      ; String srovnání
IF #2=-1 THEN NotFound           ; Numeric srovnání
IFEMPTY $3 THEN NextItem         ; Kontrola prázdnosti
```

### GOTO/LABEL - Skok
```pcs
LABEL MyLabel
  ; ... kód ...
GOTO MyLabel
```

### CALL - Volání procedury
```pcs
PROC MyProcedure
  ; ... kód ...
  RETURN
  
; V ACTION:
CALL MyProcedure
```

---

## 6. 📂 SOUBOROVÉ OPERACE

### FILEEXIST - Kontrola souboru
```pcs
FILEEXIST $filename
IF F THEN FileNotFound
```

### FILECOPY - Kopírování souboru
```pcs
FILECOPY $source $dest mode
; mode: 0=overwrite, 1=skip, 3=error handling
```

### FILEDELETE - Smazání souboru
```pcs
FILEDELETE $filename
```

### FILENAME - Extrakce jména z cesty
```pcs
FILENAME $fullpath $nameonly
; $nameonly = "file.edi" z "C:\INBOX\file.edi"
```

### PROGPATH - Získání cesty programu
```pcs
PROGPATH $basepath
; $basepath = "D:\EDICOMRP\"
```

---

## 7. 🔁 SMYČKY

### Počítadlo smyčky
```pcs
LET #1=-1              ; Inicializace na -1
LABEL NextIteration
LET #1=#1+1            ; Inkrementace
EDIGET @0 $3 "SEGMENT,1,1,,,#1"  ; Čtení s počítadlem
IFEMPTY $3 THEN EndLoop ; Konec když prázdné
; ... zpracování ...
GOTO NextIteration     ; Opakování
LABEL EndLoop
```

### Bezpečná smyčka (ochrana proti nekonečnu)
```pcs
LET #1=-1
LABEL NextItem
LET #1=#1+1
IF #1>999 THEN EndLoop ; Bezpečnostní limit
EDIGET @0 $3 "SEGMENT,1,1,,,#1"
IFEMPTY $3 THEN EndLoop
; ... kód ...
GOTO NextItem
LABEL EndLoop
```

---

## 8. 🔐 CHYBOVÉ OPERACE

### EDIVERIF - Ověření EDIFACT
```pcs
EDIVERIF @0 $result
IF F THEN InvalidEdi
```

### EDIERROR - Čtení chyby
```pcs
EDIERROR @0 $errortext
```

---

## 🎯 KOMPLEMENTÁRNÍ PŘÍKLADY

### Příklad 1: Čtení a Přepisování XML
```pcs
ACTION 1
  XMLOPEN @0 "input.xml"
  XMLTAG @0 "Root,0"
  XMLTAG @0 "Item,1"
  XMLTAG @0 "Price,2"
  XMLTEXTGET @0 $3
  LET $3=$3*1.1             ; Zvýšení ceny o 10%
  XMLTEXTSET @0 $3
  XMLSAVE @0 "output.xml"
  END
```

### Příklad 2: Iterace s Podmínkami
```pcs
ACTION 1
  EDIREAD @0 $0 0
  LET #1=-1
  LABEL NextLine
  LET #1=#1+1
  IF #1>500 THEN Complete
  EDIGET @0 $3 "LIN,1,1,,1,#1"
  IFEMPTY $3 THEN Complete
  IF $3="DELETE" THEN SkipLine
  ; ... zpracování ...
  LABEL SkipLine
  GOTO NextLine
  LABEL Complete
  END
```

### Příklad 3: Chybová Zpráva
```pcs
LABEL ErrorHandler
  LET $0="ERROR: Invalid XML format"
  RUNS "log.pcf" 1 5
  LET $0="FAILED"
  END
```

---

## 📊 Shrnutí Operací v COMDIS Skriptu

| Kategorie | Operace | Účel |
|-----------|---------|------|
| **XML** | XMLCREATE | Vytvoření nového XML |
| | XMLTAG | Navigace/Tvorba elementů |
| | XMLTEXTSET | Vložení textu |
| | XMLSAVE | Uložení XML |
| **EDI** | EDIREAD | Čtení EDIFACT |
| | EDIGET | Extrakce segmentů |
| | EDISET | Zápis do segmentů |
| **String** | STRCOPY | Manipulace textem |
| **Řídící** | IF/THEN | Podmínky |
| | LABEL/GOTO | Skoky |
| | CALL/PROC | Procedury |
| **Smyčky** | LET/#n=#n+1 | Inkrementace |
| | IFEMPTY | Test na konec |
| **Soubory** | FILEEXIST | Kontrola |
| | FILECOPY/DELETE | Manipulace |

