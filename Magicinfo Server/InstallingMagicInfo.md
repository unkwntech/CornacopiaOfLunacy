# Installing MagicInfo 9 on SQL Server without SA

The instructions below are valid if you are installing MagicInfo 9 and you do not have permissions to create databases, such as in an enterprise enviornment.  You will need a system with either SQL Server or SQL Server Express installed on in order to generate the SQL scripts that are needed to bootstrap the database, this can be the application server.

## Prerequisites

1. Database Information (server address, database name, username and password)
1. The ability to execute SQL scripts against the target database
1. Required permissions to install Web Application Server (WAS)
1. A computer with SQL Server or SQL Server Express installed (This can be the application server)
1. MagicInfo Installer

## Database Install

On the system with SQL Server or SQL Server Express, run the MagicInfo installer.  When prompted chose the "Advanced Install", "MSSQL" and "DB" options.

![Screenshot of installer showing the "Setup Type" page](https://raw.githubusercontent.com/unkwntech/CornucopiaOfLunacy/main/Magicinfo%20Server/db_setup_options.png)

Continue with the installer until prompted for the database information. Enter the databse connection information and continue.  When prompted for the WAS IP enter the IP address of the intended application server.  The remainin prompts, such as "Server Administrator Password" all applly to the web application, and not the host, this is where you are creating the application's admin account.

![Screenshot of the installer showing database settings page](https://raw.githubusercontent.com/unkwntech/CornucopiaOfLunacy/main/Magicinfo%20Server/db_config.png)

When the installer is finished it will generate some files in the install location (Default: `C:\MagicInfo Premium\`), this should consist of 4 `.sql` files and a `.bat` file.  Connect to the SQL Server and run the `.sql` scripts in the following order

1. `TableCreate.sql` - Creates tables
1. `DataInsert.sql` - Inserts the the basic data required by the application
1. `InsertOrgan.sql` - Inserts the organization and user information

## Application Install

Run the MagicInfo installer, when prompted choose the "Advanced Install", "MSSQL", and "WAS" options.

![Screenshot of installer showing the "Setup Type" page](https://raw.githubusercontent.com/unkwntech/CornucopiaOfLunacy/main/Magicinfo%20Server/was_setup_options.png)

When prompted for the database information provide the database connection details.  The field that prompts for "MSSQL Server Password" is asking for an SA account, since the database is already created there is no need for this.  However, the installer requires it, use the database user password and complete the install.