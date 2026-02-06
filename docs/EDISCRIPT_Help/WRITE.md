EDI Script - (c) EDICOM s.r.o.

# WRITE

is an instruction for writing in a text file. If the file does not exist it creates
        new file. If the file exists, the text is appended in the end of the file.

### Format:

## WRITE f t

f file name t text to write in file

### Example:

WRITE "myfile.txt" "Hello"

### See also:

[WRITEN](WRITEN.md)
