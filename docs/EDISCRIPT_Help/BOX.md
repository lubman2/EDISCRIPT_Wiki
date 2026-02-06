EDI Script - (c) EDICOM s.r.o.

# BOX

shows dialog window with specified text. Format: BOX text title flag

### Format:

## BOX text title flag

text text to show in window title title of window flag 0 = without icon 1 = stop icon 2 = question-mark icon 3 = exclamation icon 4 = information icon

### Example:

BOX "Action finished successfully" "Action" 4

        ; the function shows this window

![BOX](box.gif)

### See also:

[INBOX](INBOX.md)

[OPENBOX](OPENBOX.md)

[SAVEBOX](SAVEBOX.md)
