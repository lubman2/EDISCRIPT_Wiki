EDI Script - (c) EDICOM s.r.o.

# X12ERROR

copies the last error text in string variable.

### Format:

## X12ERROR @a $b

a ASNI X12 file pointer number (0 or 1) b string variable number

### Example:

X12EXPORT @0 $2

        IF !F THEN Label1

        X12ERROR @0 $1

        ERROR $1

### See also:

[X12READ](X12READ.md)

[X12WRITE](X12WRITE.md)

[X12COUNT](X12COUNT.md)

[X12MESSAGE](X12MESSAGE.md)
