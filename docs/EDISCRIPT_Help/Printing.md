EDI Script - (c) EDICOM s.r.o.

# Print Functions

An user can prepare his print (WYSIWYG). The print must start with a **PRINTOPEN**,
        then follows items to print, in the end is function **PRINT** or **PRINTPREVIEW**
        and the print always terminates with a **PRINTCLOSE**.

BARCODE prints barcode BITMAP prints bitmap BRUSH changes brush ELLIPSE prints ellipse FONT changes font LINE prints a line ORIENTATION sets orientation of printing PAGE creates new page PEN changes pen PRINT prints all pages PRINTCLOSE closes print buffer PRINTOPEN opens print buffer PRINTPREVIEW shows "print preview" window RECTANGLE prints rectangle ROUNDRECT prints round rectangle SETPRINTER sets default printer TEXT print text TEXTALIGN aligns text TEXTCOLOR changes color for text TEXTR print text in limited rectangle
