EDI Script - (c) EDICOM s.r.o.

# TIME

saves the current time in a numeric variable or creates the string and saves it
        in the string variable.

### Format:

## TIME v f

v numeric variable or string variable f format of string, if variable is numeric variable then f is always 0; if variable
                is string variable then it can be used numbers from table and followed by separator 0 = DDMMYYYY 1 = DDMMYY 2 = YYYYMMDD 3 = YYMMDD 4 = YYYYDDMM 5 = YYDDMM 6 = MMDDYYYY 7 = MMDDYY 8 = D 9 = M 10 = Y 11 = DDMMYYYY HH:MM 13 = day of week (1-7) 14 = YYYYMMDDHHMMSS 20 = HHMMSS 21 = HH 22 = MM 23 = SS 24 = HHMM

### Example:

TIME #8 0

        TIME $8 2

        TIME $9 24:

### See also:

[TIMETOSTR](TIMETOSTR.md)

[STRTOTIME](STRTOTIME.md)
