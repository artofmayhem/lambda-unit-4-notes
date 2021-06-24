#👋🏾👋🏾👋🏾
#Hello there! Today's lesson is in regard to....
🥁 (cue the drumroll.... )





# Database Schema Design!!  ![img_3.png](img_3.png)


## Objectives     👩🏽‍🎓 
 - learn schema design
 - set up own database

###This will be accomplished using SQLite Studio and Knex

##Topics of lecture

    - Database Management System (DBMS) -
    - SQLite Studio -
    - Primary Keys -
    - Data Types and Column Constraints -
    - Knex CLI -
    - Migrations -
    - Seeds


##By the end of these notes I should be able to: 
    - use SQlite Studio on an existing DB -
    - explain what a database schema is -
    - create and use Knex migrations
    - create and use Knex seeds



##What is a Database Management System? 🗃️

    Answer: A Graphical interface that allows us to read and manipulate a database. It is 
    an operating system on top of a hard drive. 

All database management systems are, under the hood SQL and give you access to 
select, from, where, orderBy, insert, delete, etc. 

all basically do the same but have their own sauce that makes them unique like 
Linux, Windows, iOS etc. 

SQLite is like almost all other DBMS except east to set up. 

##Why is SQLite the most used DBMS system in the world.... WHY?? 🙋🏿

    Answer: SQLite file format is stable, cross-platform, and backwards compatible. SQLite database
    files are commonly used as containers to transfer rich content between systems. it is installed in 
    every mobile device in the world. db3 files are super transportable. 


##What is PostgreSQL? 

    Answer: PostgreSQL is an open source object-relational database system with over 30 years of active 
    development. Hipster DBMS. Has support for a data type that allowsd us to write unstructured json to    
    the database. It took the best of mongoDB and MySQL and combined them into a powerful system

##MySQL 
    
    Answer: Not open source. more corporate including github, facebook, ebay, twitter, and Tesla. 
    There is a free version that most people use and a paid enterprise edition. Made by Oracle

##What is a Database schema? 

    Answer: it's the shape or structure of the database. What it's going to look like


### Data types
    - string, numeric, date, time, char, boolean, binary, text, tinyblob (Binary Large OBjects)etc... 


###Not Null - some distinctions are NOT NULL, 
###Primary Key is typically an id in our usage. 
###AutoIncrement adds a 1 to the value each time in giving something like a new id number. 

##planning stage of database is mission critical. Changing at a later time is possible but def not ideal


Simple Knex file set up

###knexfile.js


// Update with your config settings.

    module.exports = {
        development: {
            //RDBMS
            client: 'sqlite3',
            connection: {
                    filename: './data/produce.db3'
                },
            useNullAsDefault: true
        },
    };

###db-config.js

    const knex = require('knex');
    const config = require('../knexfile')
    const db = knex(config.development)

##What is a migration? ✈️

    Answer: initial schema. migration... all developer on the team should have the same 
    schema on their local. THis allows us to commit to github. as a developer i can fork and clone 
    and it will auto set up across all machines. also set up staging and production databases
    when the time comes. way to update the structure of the database. a little tricky at first. 

###If you spend a good amount of time in planning you won't be migrating alot. 

##
##

###To initiate a new migration in the terminal of your root folder. 

    knex migrate:make

the return is a migrations folder with representations of protractive and retractive migration states

    //applies to forward changes
    exports.up = function(knex) {
    
    };
    //applies to rollback changes
    exports.down = function(knex) {
    
    };

This is a basic example of how to build a table for migrations

    //applies to forward changes
exports.up = function(knex, Promise) {

    return knex.schema.createTable('fruits', tbl => {
        tbl.increments() //defaults to id
        // name, avgWeightOz, delicious
        tbl.text('name', 128).unique().notNullable();
        tbl.float('avgWeightOz').notNullable();
        tbl.boolean('delicious').defaultTo(false);
    })
        };
        //applies to rollback changes
        exports.down = function(knex, Promise) {
        return knex.schema.dropTableIfExists("fruits");
        };

documentation for knex can be found here: 

    https://knexjs.org/

###To create migration database and table 
    
    knex migrate:latest

###To make a seed

    knex seed:make fruits

###go into seeds and add sample seed data in schema format


###To run

    knex seed:run

if you run it twice different ids will come back

truncate() resets id

![img_4.png](img_4.png)