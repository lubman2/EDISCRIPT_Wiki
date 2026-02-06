EDI Script - (c) EDICOM s.r.o.

# WRITEN

is an instruction for writing in the text file. If the file does not exist it creates
        a new file. If the file exists the text is appended in the end of the file. The
        text is terminated with the characters CRLF for a new line.

### Format:

## WRITEN f t

f file name t text to write in file

### Example:

WRITEN "myfile.txt" "Hello"

### See also:

[WRITE](WRITE.md)
