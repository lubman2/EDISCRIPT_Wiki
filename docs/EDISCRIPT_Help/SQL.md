EDI Script - (c) EDICOM s.r.o.

# SQL Functions

enable to work with database tables using ODBC. User can work with SQL Server. User
        can prepare ODBC connection to his database an then use SQL functions to exchange
        data. **SQLCONNECT** must be first function. Connection is closed with **SQLCLOSE**.

SQLCONNECT starts SQL connection SQLEXEC executes SQL command SQLSELECT executes command SELECT SQLFETCH reads one line from table after command SELECT SQLGET gets value from table after command SELECT SQLSET sets value for command SQLEXEC SQLERROR returns error string from SQL command SQLCLOSE closes SQL connection
