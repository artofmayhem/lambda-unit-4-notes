## Intro to relational databases
## Basics of SQL (Structured Query Language)
## SELECT, INSERT, UPDATE, DELETE queries in SQL
## Setup Knex.js
## SELECT, INSERT, UPDATE, DELETE queries using Knex

* Goals * 
* explain what relational database is and it's core components
* explain what SQL is and its advantages
* Q, I and U data in SQL
* write db queries using knex.js

## What is a database?
 - central repository of where data is stored

## What is a relational database? 
 - defacto database
 - groups of data grouped into a table with a field or column (key value pair).
 - related data.... do users.... or projects... or artists and each one has their own info. 
    this is the beginning of understanding the terminology of the API

Types mySQL, SQL, SQLite, postgres (lambda preference) Oracle

## What is noSQL
    - mongoDB stores json objects in the database
    

## What is a table in a database
It's rows and columns of data (excel much?). organized information

Initial SQL statement - (point of note) => SQL runs with multiline functionality so ; is always used to end a query not a line and Commands are Capitalized

** Select is used 80-90% of the time (GET Request handler) **

SELECT * FROM Customers; // grab * (everything) from database and.. 
SELECT CustomerName, Address from Customers; grab only these two key/ value pairs and display

    Select * 
    FROM Customers
    WHERE ContactName = "Ana Trujillo" 
    or Country = "Canada" 
    or Country = "USA";  // syntax variations or / >/ < / =

    Select * 
    FROM Customers
    WHERE Country = "Mexico" and PostalCode < "05033" 
    ORDER By PostalCode desc
    LIMIT 1;

** INSERT (Post request handler) **
INSERT INTO Customers (Country, CustomerName, ContactName, Address, City, PostalCode)
VALUES ("USA", "SONVR Design", "Tony Miller", "3672 Woodlawn Dr", "Honolulu", "96822");

  ** order matters in assigning values to corresponding key pairing

** UPDATE (PUT request handler) **
UPDATE dataBase
SET Key = Value
WHERE keyToBeChanged = Value;

always include an ID or identifier otherwise you can affect the entire data table by giving them all the same value. 

** DELETE (DELETE request handler) ** 
DELETE FROM dataBase
WHERE Key = Value;

** Order
ORDER BY CustomerName ASC;  display the data by the customer name in ASC or DESC (descending) order 




