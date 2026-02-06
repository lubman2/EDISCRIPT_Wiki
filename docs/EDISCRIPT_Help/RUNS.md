EDI Script - (c) EDICOM s.r.o.

# RUNS

runs other script file. EDIFACT, numeric, floating point and string registers are
        copied to new script according a parameter p. A flag is set if error happened.

### Format:

## RUNS "scrip.pcf" a p

script.pcf script file name with extension .pcf a action number p parameter: bit 0 (1) - copy EDIFACT pointer to new script bit 1 (2) - copy all/no registers to new script bit 2 (4) - copy registers $0, #0; if bit 1 is set, registers $1 and #1 are also
                copied

### Example:

RUNS "myscript.pcf" 1 3

### See also:

[PROGPATH](PROGPATH.md)

[RUN](RUN.md)

[RUNX](RUNX.md)

[RUNEX](RUNEX.md)
