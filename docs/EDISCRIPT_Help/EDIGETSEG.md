EDI Script - (c) EDICOM s.r.o.

# EDIGETSEG

gets a specified segment and level from the file opened by function EDIREAD. The
        flag is on set if error happens.

### Format:

## EDIGETSEG @a b $c #d

a EDIFACT file pointer number (0 or 1) b number or numeric register for segment number c string register number for retrieved segment d numeric register number for retrieved level

### Example:

EDIREAD @0 "test.edi" 1

        EDIGETSEG @0 #1 $L #2

### See also:

[EDIREAD](EDIREAD.md)

[EDIGETSEGS](EDIGETSEGS.md)

[EDIMESSAGE](EDIMESSAGE.md)
