EDI Script - (c) EDICOM s.r.o.

# INBOX

shows a dialog box for input. The script stops and wait for a user action. The user
        can set a title, a text and a default value in this window. If the user press OK
        button, the function returns the text written by the user. If the user cancel the window flag is set.
	Do not use this function in server mode!

### Format:

## INBOX text title default register

text string variable or constant with text of inbox title string variable or constant with title of inbox window default string variable or constant with default text in edit window register register for returning value

### Example:

INBOX "Value" "Test" "100" #3

        ; the function shows this window

![Inbox](inbox.gif)

### See also:

[BOX](BOX.md)

[OPENBOX](OPENBOX.md)

[SAVEBOX](SAVEBOX.md)
