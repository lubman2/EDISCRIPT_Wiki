EDI Script - (c) EDICOM s.r.o.

# XMLCLOSE

closes and release XML object from a memory.

### Format:

## XMLCLOSE @a

a XML file pointer number (0 or 1)

### Example:

XMLOPEN @0 "test.xml"

        IF !F THEN Label1

        EDIERROR @0 $1

        BOX $1 "Error" 1

        END

        LABEL Label1

        ...

        XMLCLOSE @0

### See also:

[XMLOPEN](XMLOPEN.md)

[XMLERROR](XMLERROR.md)
