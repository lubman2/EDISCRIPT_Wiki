EDI Script - (c) EDICOM s.r.o.

# EDIFACT Navigation

is a string which describes how to find a value from the EDIFACT message or where
        to save the value in the EDIFACT message. Items in the string are separated by ","
        (comma). There must not be spaces between items or commas.

### Format:

"u,seg,e,s,t,l,r,fe1,fs1,fv1,fe2,fs2,fv2,fe3,fs3,fv3"

u segments group, conditional; 0 = default, search starts from first segment; 1 =
                search start after segment UNS+D'; 2 = search starts after segment UNS+S' seg segment tag, segment has 3 capital letters or character = switch means that segment
                is the same like in previous function EDIGET, EDISET or EDIFATHER e element number, means how many + are in front of item s sub element number, means how many : are in front of item plus 1, + resets value
                to 1 t short file name of table for conversion, conditional, default value is empty, value
                is searched in first column of dbf table and if value is found value from second
                column is retrieved, slash (/) with number after table name means a column of the
                table l level, conditional, default = 0, level means level of nested segments (0,1, 2, ...) r repeat, conditional, default = 0, repeat means repeat of segment (0, 1, 2, ...),
                -1 is next repeat fe1, fe2, fe3 filter element, conditional if not used, similar to e fs1, fs2, fs3 filter sub element, conditional if not used, similar to s fv1, fv2, fv3 filter value, conditional if not used

### Example:

EDIFACT message:

        UNB+UNOA:2+0000000000001:14+0000000000002:14+970404:1400+1'

        UNH+161+ORDERS:D:93A:UN:EAN007'

        BGM+220+161'

        DTM+137:19960924:102'

        DTM+2:19960929:102'

        DTM+2:1000:401'

        NAD+SU+0000000000003::9'

        NAD+DP+0000000000004::9'

        NAD+BY+0000000000005::9'

        LIN+1++0000000000006:EN'

        QTY+21:3'

        LIN+2++0000000000007:EN'

        QTY+21:99'

        LIN+3++0000000000008:EN'

        QTY+21:4'

        UNS+S'

        CNT+1:12'

        UNT+17+161'

        UNZ+1+1'

### Values:

"UNH,2,1" ; "ORDERS"

        "UNH,2,3" ; "93A"

        "DTM,1,2,,0,0,1,1,2,1,3,102" ; "19960929"

        "DTM,1,2,,,,1,1,2,1,3,401" ; "1000"

        "LIN,3,1,,,1" ; "00000000000007"

        "QTY,1,2,,1,0,1,1,21" ; "99"

        "2,CNT,1,2,,,,1,1,1" ; "12"
