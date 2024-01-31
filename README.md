# Bus_Booking_System

Creating a bus booking system in Python involves designing a program that allows users to search for buses, choose seats, and make reservations.
using Python with Tkinter for the GUI and SQLite for data storage.

Install Required Libraries:

Make sure you have Tkinter installed. If you are using Python 3, Tkinter should be included by default.

Install SQLite3 if not already installed:

- pip install sqlite3

Create Database:

Create a SQLite database to store bus information and reservations.
python
Copy code
import sqlite3

# Connect to the database (creates a new one if it doesn't exist)

connection = sqlite3.connect("bus_booking.db")
cursor = connection.cursor()

# Create a Bus table

cursor.execute('''
CREATE TABLE IF NOT EXISTS buses (
id INTEGER PRIMARY KEY,
destination TEXT,
departure_time TEXT,
total_seats INTEGER,
available_seats TEXT
)
''')

# Create a Reservations table

cursor.execute('''
CREATE TABLE IF NOT EXISTS reservations (
id INTEGER PRIMARY KEY,
bus_id INTEGER,
username TEXT,
seat_number INTEGER,
FOREIGN KEY (bus_id) REFERENCES buses(id)
)
''')

# Commit and close the connection

connection.commit()
connection.close()
