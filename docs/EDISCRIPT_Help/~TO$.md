EDI Script - (c) EDICOM s.r.o.

# ~TO$

converts a floating point value to a string.

### Format:

## ~TO$ ~a $b "0x.y"

a number for floating point variable, 0..2 b number for string variable, 0..9, L 0 If the output value has less than a characters, it is filled on the left with zeros. x At least n characters are printed. If the output value has less than n characters,
                the output is padded with blanks (right-padded if - flag given, left-padded otherwise).
                number of numeric characters in front of floating point y y characters or y decimal places are printed. If the output value has more than
                n characters, the output might be truncated or rounded. (Whether this happens depends
                on the type character.)

### Example:

LET ~0=3.14

        ~TO$ ~0 $0 "7.4" ; *" 3.1400"*

        ~TO$ ~0 $0 "08.1" ; *"000003.1"*

### See also:

[LET](LET.md)
