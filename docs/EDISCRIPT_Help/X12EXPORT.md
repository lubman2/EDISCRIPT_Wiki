EDI Script - (c) EDICOM s.r.o.

# X12EXPORT

exports an ANSI X12 message in ASCII or database file. Description of how to export
        is in a receipt file. This file can be created with Mapper.exe. If an export is
        not successful the flag is set on.

### Format:

## X12EXPORT @a r [p]

a ANSI X12 file pointer number (0 or 1) r string, register or constant with receipt file name p path for exported data files, the item is not mandatory

### Example:

X12READ @0 "test.X12" 1

        X12EXPORT @0 "ordersex.rcp"

        IF F THEN err

        END

        LABEL err

        X12ERROR @0 $7

        ERROR $7

### See also:

[X12READ](X12READ.md)

[X12IMPORT](X12IMPORT.md)

[X12WRITE](X12WRITE.md)
