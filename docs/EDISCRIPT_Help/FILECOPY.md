EDI Script - (c) EDICOM s.r.o.

# FILECOPY

copies a file. The flag is set on if an error happens.

### Format:

## FILECOPY s d f

s string, string variable or constant for source file name d string, string variable or constant for destination file name f flag, bit combination bit 0 (1) = overwrite bit 1 (2) = delete source bit 2 (4) = append

### Example:

FILECOPY "test.edi" "newfile.edi" 6 ; append and delete source (2+4)

### See also:

[FILEDELETE](FILEDELETE.md)

[FILEEXIST](FILEEXIST.md)

[FILENAME](FILENAME.md)

[FILEUNIQUE](FILEUNIQUE.md)
