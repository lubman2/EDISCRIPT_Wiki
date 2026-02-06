EDI Script - (c) EDICOM s.r.o.

# XMLTAG

searches for specified tag in a XML document and set pointer to this tag The flag
        is set on if an error happens.

### Format:

## XMLTAG @a "tag,level,repeat"

a XML file pointer number (0 or 1) tag tag name to search level level of nested segments (0, 1, 2, ...) repeat repeat of segment

### Example:

XMLOPEN @0 "test.xml"

        IF !F THEN Label1

        EDIERROR @0 $1

        BOX $1 "Error" 1

        END

        LABEL Label1

        XMLTAG @0 "item,0"

        ...

        XMLCLOSE @0

### See also:

[XMLCLOSE](XMLCLOSE.md)

[XMLERROR](XMLERROR.md)

[XMLTAGSET](XMLTAGSET.md)
