EDI Script - (c) EDICOM s.r.o.

# X12IMPORT

creates an ANSI X12 message from ASCII or database file. Description of how to convert
        is in a receipt file. This file can be created with the program Mapper.exe. The
        flag is set on if error happens.

### Format:

## X12IMPORT @a r [p]

a ANSI X12 file pointer number (0 or 1) r string, string variable or constant with receipt file name p path with data files, the item is not mandatory

### Example:

X12IMPORT @0 "ordersim.rcp"

        IF !F THEN Write

        X12ERROR @0 $7

        ERROR $7

        LABEL Write

        X12WRITE @0 "test.X12" 4

        IF !F THEN End

        ERROR "Cannot write in test.X12"

        LABEL End

        ...

### See also:

[X12EXPORT](X12EXPORT.md)

[X12READ](X12READ.md)

[X12COUNT](X12COUNT.md)
