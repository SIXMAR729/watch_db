Safe Interactive SQLite Client
A simple, safe, and interactive command-line client for managing SQLite databases directly. This tool is designed for developers who need to quickly view or modify a SQLite database without installing a full database management application like DB Browser for SQLite.

Why Use This Tool?
No Installation Needed: Manage your SQLite database using a single Python script. No need to install and open a separate GUI application.

Prevent Mistakes: The client includes safety features to prevent accidental data modification or deletion.

Read-Only Mode: Start the client in a mode that blocks all data-changing commands (DELETE, UPDATE, INSERT, etc.).

Confirmation Prompts: Even in full-access mode, the client will ask for confirmation before executing a potentially destructive command.

User-Friendly Output: SELECT query results are printed in a clean, easy-to-read table format.

Features
Interactive SQL Shell: Run any standard SQL command directly from your terminal.

Two Access Modes:

Full Access (Default): Execute any SQL command, with safety prompts for modifying commands.

Read-Only Mode: A secure mode that only allows data-viewing commands like SELECT.

Robust Error Handling: Catches and displays SQL errors gracefully without crashing.

Clean Connection Management: Ensures the database connection is always closed properly on exit.

Requirements
Python 3.x

A SQLite database file. The script is pre-configured to look for a database at ./order.db. You can change the DATABASE_NAME variable in the script to point to your own database file.

How to Use
Clone or download the repository.

Make sure your database file is in the correct location (e.g., in a db/ folder).

Open your terminal and navigate to the project directory.

To run in Full Access Mode:
Execute the script without any arguments. You will be warned before running any command that can modify data.
'''bash'''
python watch_db.py
'''
To run in Read-Only Mode:
Use the --read-only flag. In this mode, any attempt to run a destructive command will be blocked.

python watch_db.py --read-only

To exit the client:
Type .quit and press Enter.

sql> .quit

Example Session
Here is an example of what a session might look like.

$ python your_script_name.py
🔎 Connected to database: ./db/hotelsystem.db (Mode: Full Access)
Enter any SQL command, or type '.quit' to exit.

sql> SELECT id, name, price_per_night FROM rooms WHERE type = 'Suite';
id                  | name                | price_per_night
-------------------------------------------------------------------
101                 | Presidential Suite  | 500
205                 | Junior Suite        | 250

sql> DELETE FROM bookings WHERE booking_id = 4;
⚠️ This command can modify data. Are you sure? [y/N] y
✅ OK. Rows affected: 1

sql> .quit

Disconnected from database.
