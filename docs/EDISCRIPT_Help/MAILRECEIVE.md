EDI Script - (c) EDICOM s.r.o.

# MAILRECEIVE

receives emails from a specified email address using protocol POP3. The flag is
        set if an error happened.

### Format:

## MAILRECEIVE "Server" "UserName" "Password" "Original" "Text" "Attach"

Server address of POP3 server UserName user name Password password for user name Original path for original messages, whole messages Text path for text separated from messages Attach path for files attached to messages

### Example:

MAILRECEIVE "pop3.server.com" "Test" "password" "Original" "Text" "Attach"

        IF F THEN error

        ...

        LABEL error

### See also:

[MAIL](MAIL.md)

[INIRERAD](INIRERAD.md)
