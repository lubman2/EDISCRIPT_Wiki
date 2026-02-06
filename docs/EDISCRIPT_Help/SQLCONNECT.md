EDI Script - (c) EDICOM s.r.o.

# SQLCONNECT

opens an SQL connection. The SQL connection must be closed by function SQLCLOSE.

### Format:

## SQLCONNECT s

s string for connection string

**The connection string uses the following keywords:**

DSN The name of the data source as it is returned by SQLDataSources. The DSN keyword
                is not used if the DRIVER keyword is used. DRIVER The name of the driver as returned by SQLDrivers. The DRIVER keyword is not used
                if the DSN keyword is used. The SQL Server driver name is {SQL Server}. (For a 16-bit
                program, the 32-bit driver name is {SQL Server (32 bit)}.) SERVER The name of the server on the network on which the data source resides. When running
                on Microsoft Windows NT, "(local)" can be entered as the server, in which case,
                a local copy of SQL Server can be used, even when this is a non-networked version.
                Note that when the 16-bit SQL Server driver is using "(local)" without a network,
                the "MS Loopback Adapter" must be installed. UID The user login ID. PWD The user-specified password. APP The name of the application calling SQLDriverConnect (optional). WSID The workstation ID. Typically, this is the network name of the computer on which
                the application resides (optional). DATABASE The name of the SQL Server database (optional). LANGUAGE The national language to be used by SQL Server (optional).

### Example:

SQLCONNECT "DRIVER=SQL Server;SERVER=TEST;WSID=TEST;Database=MY_DATA"

        IF !F THEN Exec

        END

        LABEL Exec

        ...

        SQLCLOSE

### See also:

[SQLCLOSE](SQLCLOSE.md)

[SQLERROR](SQLERROR.md)

[SQLSELECT](SQLSELECT.md)

[SQLEXEC](SQLEXEC.md)
