EDI Script - (c) EDICOM s.r.o.

# X12CHECK

checks for the syntax errors in the message and looks for the mandatory fields in
        the message. Description of the mandatory fields is in the receipt file. If there
        is an error in the message, the ANSI X12 error message is created according err.rcp.
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

## X12CHECK @a @e r

a ANSI X12 file pointer number for tested message e ANSI X12 file pointer number for error message r receipt file name

### Example:

X12IMPORT @0 "invoic.rcp"

        IF !F THEN Check

        X12ERROR @0 $0

        ...

        END

        LABEL Check

        X12RESET @1

        X12CHECK @0 @1 "invoicch.rcp"

        IF !F THEN TestErr

        X12ERROR @0 $0

        ...

        END

        LABEL TestErr

        X12GET @1 #4 "CNT,1,2,,,,1,1,2"

        IF #4=0 THEN Write

        X12WRITE @1 "error.X12" 1

        IF !F THEN End

        X12ERROR @1 $0

        ...

        END

        LABEL Write

        X12WRITE @0 "out.X12" 6 IF !F THEN End X12ERROR @0 $0 ...

        LABEL End

        END

### See also:

[X12READ](X12READ.md)

[X12IMPORT](X12IMPORT.md)

[X12WRITE](X12WRITE.md)

[X12ERROR](X12ERROR.md)
