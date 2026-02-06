EDI Script - (c) EDICOM s.r.o.

# EDIWRITE

saves EDIFACT message(s) in file. The flag is set on if an error happens.

### Format:

## EDIWRITE @a f x

a EDIFACT file pointer number (0 or 1) f file name x bit parameters: bit 0 (1) - 1 = overwrite; 0 = do not overwrite, error happens if file exist bit 1 (2) - 1 = one message only; 0 = all messages; bit 2 (4) - 1 = append bit 3 (8) - 1 = save according setting (next bits); 0 = save message as it is bit 4 (16) - 1 = save UNA segment if exist; 0 save without UNA segment bit 5 (32) - 1 = save UNB segment if exist; 0 save without UNB segment bit 6 (64) - 1 = save UNG segment if exist; 0 save without UNG segment bit 7 (128) - 1 = save segments from selected UNB to UHT

### Example:

EDIWRITE @0 "test.edi" 4 ; append all messages

        ...

        EDIWRITE @0 "test0.edi" 6 ; append one message only

### See also:

[EDIREAD](EDIREAD.md)

[EDICOUNT](EDICOUNT.md)
