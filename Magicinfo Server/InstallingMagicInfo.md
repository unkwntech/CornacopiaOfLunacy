# Installing MagicInfo 9 on SQL Server without SA

The instructions below are valid if you are installing MagicInfo 9 and you do not have permissions to create databases, such as in an enterprise enviornment.  You will need a system with either SQL Server or SQL Server Express installed on in order to generate the SQL scripts that are needed to bootstrap the database, this can be the application server.

## Prerequisites

1. Database Information (server address, database name, username and password)
1. The ability to execute SQL scripts against the target database
1. Required permissions to install Web Application Server (WAS)
1. A computer with SQL Server or SQL Server Express installed (This can be the application server)
1. MagicInfo Installer

## Database Install

On the system with SQL Server or SQL Server Express, run the MagicInfo installer.  When prompted (https://i.imgur.com/9jTQtVi.png) chose the "Advanced Install", "MSSQL" and "DB" options.  Continue with the installer until prompted for the database information (https://i.imgur.com/xsMPoiH.png). Enter the databse connection information and continue.  When prompted for the WAS IP enter the IP address of the intended application server.  The remainin prompts, such as "Server Administrator Password" all applly to the web application, and not the host, this is where you are creating the application's admin account.

When the installer is finished it will generate some files in the install location (Default: `C:\MagicInfo Premium\`), this should consist of 4 `.sql` files and a `.bat` file.  Connect to the SQL Server and run the `.sql` scripts in the following order

1. `TableCreate.sql` - Creates tables
1. `DataInsert.sql` - Inserts the the basic data required by the application
1. `InsertOrgan.sql` - Inserts the organization and user information

## Application Install

Run the MagicInfo installer, when prompted (https://i.imgur.com/Upfh2zb.png) choose the "Advanced Install", "MSSQL", and "WAS" options. When prompted for the database information provide the database connection details.  The field that prompts for "MSSQL Server Password" is asking for an SA account, since the database is already created there is no need for this.  However, the installer requires it, use the database user password and complete the install.