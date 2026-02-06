EDI Script - (c) EDICOM s.r.o.

# EDI Script Introduction

Script files are possible to create with program "EdiScrpt.exe". Default extension
        for script file is .pcs. Compilation creates two files: .pcf is code file used in
        programs and .deb file with debug information for tracing instructions.

Every line of the script file must start with a keyword which must be written in
        capital letters and must start on first position in line. The following comment
        - if there is one - must start with this character ";". The program always starts
        with a keyword "ACTION x" and terminates with keywords END or ERROR.

        In a single script file can be more then one keyword ACTION. It is recommended to
        use the comment after keyword ACTION. The following comment must be on the same
        line. Example:

        ACTION 1 ; Import

        This comment is important for some programs. The programs show the user this text
        in a selection box. EDIFACT script use string, numeric, floating point variables,
        EDIFACT pointers and flag. These variables are available during the action, but
        their values are not available for the next execution. Usually all variables are
        0 and strings are empty. In some programs some values are set before the start of
        the first keyword. See also other helps.

### See also:

[Variables](Variables.md)

[Keywords](Keywords.md)
