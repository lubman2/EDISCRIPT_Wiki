EDI Script - (c) EDICOM s.r.o.

# X12WRITE

saves ANSI X12 message(s) in file. The flag is set on if an error happens.

### Format:

## X12WRITE @a f x

a ANSI X12 file pointer number (0 or 1) f file name x bit parameters: bit 0 (1) - 1 = overwrite; 0 = do not overwrite, error happens if file exist bit 1 (2) - 1 = one message only; 0 = all messages; bit 2 (4) - 1 = append bit 3 (8) - 1 = save according setting (next bits); 0 = save message as it is bit 4 (16) - 1 = save UNA segment if exist; 0 save without UNA segment bit 5 (32) - 1 = save UNB segment if exist; 0 save without UNB segment bit 6 (64) - 1 = save UNG segment if exist; 0 save without UNG segment bit 7 (128) - 1 = save segments from selected UNB to UHT

### Example:

X12WRITE @0 "test.X12" 4 ; append all messages

        ...

        X12WRITE @0 "test0.X12" 6 ; append one message only

### See also:

[X12READ](X12READ.md)

[X12COUNT](X12COUNT.md)
