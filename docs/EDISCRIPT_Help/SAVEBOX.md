EDI Script - (c) EDICOM s.r.o.

# SAVEBOX

shows an "Save File" dialog box for selecting or creating file name. A flag is set
        on if user press button "Close".

### Format:

## SAVEBOX $a $b

a string register for the file name b string or string register with label of box, if string is empty default label is
                used

### Example:

SAVEBOX $0 ""

        IF !F THEN Save

        END

        LABEL Save

        ...

### See also:

[OPENBOX](OPENBOX.md)

[BOX](BOX.md)

[INBOX](INBOX.md)
