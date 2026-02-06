EDI Script - (c) EDICOM s.r.o.

# TIMETOSTR

converts a numeric value of time to a string

### Format:

## TIMETOSTR #a $b f

a numeric variable number b string variable number f format of string, There can be numbers from table followed by separator 0 = DDMMYYYY 1 = DDMMYY 2 = YYYYMMDD 3 = YYMMDD 4 = YYYYDDMM 5 = YYDDMM 6 = MMDDYYYY 7 = MMDDYY 8 = D 9 = M 10 = Y 11 = DDMMYYYY HH:MM 13 = day of week (1-7) 14 = YYYYMMDDHHMMSS 20 = HHMMSS 21 = HH 22 = MM 23 = SS 24 = HHMM

### Example:

TIME #3 0

        TIMETOSTR #3 $4 1.

### See also:

[STRTOTIME](STRTOTIME.md)

[TIME](TIME.md)
