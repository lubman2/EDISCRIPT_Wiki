EDI Script - (c) EDICOM s.r.o.

# STRTOTIME

converts the string to the numeric value of time. The instruction sets the flag
        if the conversion is not successful.

### Format:

## STRTOTIME $a #b f

a string variable number b numeric variable number f format of string, There can be numbers from table followed by separator 0 = DDMMYYYY 1 = DDMMYY 2 = YYYYMMDD 3 = YYMMDD 4 = YYYYDDMM 5 = YYDDMM 6 = MMDDYYYY 7 = MMDDYY 8 = D 9 = M 10 = Y 11 = DDMMYYYY HH:MM 12 = YYYYWW 13 = day of week (1-7) 14 = YYYYMMDDHHMMSS 20 = HHMMSS 21 = HH 22 = MM 23 = SS 24 = HHMM

### Example:

LET $3="22.02.2000"

        STRTOTIME $3 #4 0.

### See also:

[TIMETOSTR](TIMETOSTR.md)

[TIME](TIME.md)
