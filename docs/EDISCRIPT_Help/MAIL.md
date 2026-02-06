EDI Script - (c) EDICOM s.r.o.

# MAIL

sends e-mail to a specified e-mail address. The flag is set if an error happened.

### Format:

## MAIL "Server" "From" "To" "Subject" "Text" "File" "UserName" "Password"

Server address of SMTP server From e-mail address of sender To e-mail address of receiver Subject Subject of message Text text of message File file name for attached file UserName user name, can be empty string Password password for user name, can be empty string

### Example:

MAIL "smtp.server.com" "ediserver@myfirm.com" "admin@myfirm.com" "Error" "Communication
        error" "" "" ""

### See also:

[INIREAD](INIREAD.md)
