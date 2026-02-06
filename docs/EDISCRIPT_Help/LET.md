EDI Script - (c) EDICOM s.r.o.

# LET

is a basic instruction for changing value of variables. A left site of equation
        must always be a variable, the right part can be a variable, constant, string or
        number split by an arithmetic sign. There must not be any spaces in the equation.
        There is an automatic conversion according to a variable in the left part of the
        equation. Absorber is character '?'.

### Format:

## LET va=r

v variable type ($, #, ~) a variable number r right part of equation with +, -, *, / between variables, constants, numbers and
                strings

### Example:

LET $1="Test"

        LET #1=5

        LET ~0=3.14

        LET $2=$1+" "+#1+" = "+~0

### See also:

[Variables](Variables.md)

[IF](IF.md)

[SWITCH](SWITCH.md)
