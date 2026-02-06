EDI Script - (c) EDICOM s.r.o.

# XMLERROR

retrieves an error text if the error happens during opening an XML file.

### Format:

## XMLERROR @a f

a XML file pointer number (0 or 1) f string variable for an error text

### Example:

XMLOPEN @0 "test.xml"

        IF !F THEN Label1

        XMLERROR @0 $1

        BOX $1 "Error" 1

        END

        LABEL Label1

        ...

        XMLCLOSE @0

### See also:

[XMLCLOSE](XMLCLOSE.md)

[XMLOPEN](XMLOPEN.md)
