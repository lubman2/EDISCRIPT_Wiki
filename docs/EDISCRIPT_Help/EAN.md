EDI Script - (c) EDICOM s.r.o.

# EAN

check a last number in EAN number or adds the last number if the number does not
        exist. A flag is set if EAN number is not correct. If the EAN number has 12 numbers
        only last number is calculated and put in the end of string.

### Format:

## EAN s

s string with EAN number

### Example:

EAN "123456789012"

        IF F THEN Error

        ...

        LABEL Error

        ...

### See also:

[IF](IF.md)

[LABEL](LABEL.md)
