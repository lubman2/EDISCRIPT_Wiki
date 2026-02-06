EDI Script - (c) EDICOM s.r.o.

# OPENBOX

shows an "Open File" dialog box for selecting a file name. A flag is set on if user
        press button "Close".

### Format:

## OPENBOX $a $b

a string register for the file name b string or string register with label of box, if string is empty default label is
                used

### Example:

OPENBOX $0 ""

        IF !F THEN Open

        END

        LABEL Open

        ...

### See also:

[SAVEBOX](SAVEBOX.md)

[BOX](BOX.md)

[INBOX](INBOX.md)
