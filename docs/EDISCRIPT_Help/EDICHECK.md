EDI Script - (c) EDICOM s.r.o.

# EDICHECK

checks for the syntax errors in the message and looks for the mandatory fields in
        the message. Description of the mandatory fields is in the receipt file. If there
        is an error in the message, the EDIFACT error message is created according err.rcp.
        The flag is set on if error happens. The function can saves following values in
        error message according settings in err.rcp file:

        Conditions: Check Value: \N Number of lines

        Conditions: Check Value: \E Error code

        Conditions: Check Value: \D Error description

        Conditions: Check Value: \R Error reference

        Conditions: Check Value: UNH,2,1 Message type of checked message

        Conditions: Check Value: BGM,2,1 Number of checked message

        Conditions: Check Value: DTM,1,2,,,,1,1,137 Date of checked message

        If there is used a script in receipt file, the script has to return 0 in variable
        #1 or 1 if error was found. There must be an error message in variable $1 then.

### Format:

## EDICHECK @a @e r

a EDIFACT file pointer number for tested message e EDIFACT file pointer number for error message r receipt file name

### Example:

EDIIMPORT @0 "invoic.rcp"

        IF !F THEN Check

        EDIERROR @0 $0

        ...

        END

        LABEL Check

        EDIRESET @1

        EDICHECK @0 @1 "invoicch.rcp"

        IF !F THEN TestErr

        EDIERROR @0 $0

        ...

        END

        LABEL TestErr

        EDIGET @1 #4 "CNT,1,2,,,,1,1,2"

        IF #4=0 THEN Write

        EDIWRITE @1 "error.edi" 1

        IF !F THEN End

        EDIERROR @1 $0

        ...

        END

        LABEL Write

        EDIWRITE @0 "out.edi" 6 IF !F THEN End EDIERROR @0 $0 ...

        LABEL End

        END

### See also:

[EDIREAD](EDIREAD.md)

[EDIIMPORT](EDIIMPORT.md)

[EDIWRITE](EDIWRITE.md)

[EDIERROR](EDIERROR.md)
