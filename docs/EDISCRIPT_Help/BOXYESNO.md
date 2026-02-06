EDI Script - (c) EDICOM s.r.o.

# BOXYESNO

shows dialog window with buttons Yes and No. If the button No is pressed the flag
        is set.

### Format:

## BOXYESNO text title

text text of message title title of window

### Example:

BOXYESNO "Test??" "EDI"

        IF F THEN No

        LET $0="Yes"

        LABEL No

        LET $0="No"

### See also:

[BOX](BOX.md)

[INBOX](INBOX.md)
