EDI Script - (c) EDICOM s.r.o.

# IF

is the basic test. The program continues according to the result of the test. If
        the result of the test is TRUE, the program continues on line with the same label
        which is after THEN. If the result of the test is FALSE the program continues on
        the next line.

### Format:

## IF e THEN a

e equation with =, !=, <, >, <=, >=, F (flag) or !F (not flag) a name of label to jump if result of equation is true

### Example:

LET #1=1

        LET #2=5

        IF #1>#2 THEN a1

        LET $0="test" IF $1!=$0 THEN a1

        ...

        IF !F THEN a1

        ...

        LABEL a1

        ...

### See also:

[LET](LET.md)

[LABEL](LABEL.md)

[Variables](Variables.md)
