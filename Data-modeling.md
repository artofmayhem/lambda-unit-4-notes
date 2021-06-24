#🗃️🗃️🗃️🗃️

#Data Modeling 😎

##Objectives: 
    - explain data normalization
    - explain different table relationships
    - create table relationships using Knex

##What is Data Normalization 🧐

###at best  🤗
- a well designed data base makes life a joy

###at worst 😓
- it will destroy your company

#Rules for tables  📏     
    DO   ✔️
        - design it so that everyone understands what it represents. By "everyone" I mean EVERYONE
        - use plural for the table name
        - represents a subject or an appointnet
        - Each record has an Artifical Primary key    MUST DO!!!
        - No redundant entries

    Don't 🛑
        - Duplicate columns (email1, email2, etc)
        - acronyms or abbreviations in table name
        - ambiguous table name (data, table, value, etc)


#Rules for Columns 🏛️

     DO   ✔️
        - Unique name that appears once in a db
        - represents a specific characteristic of subject
        - holds a single value
        - THe primary key represents the subject
        - The non primary keys describe the pk

    Don't 🛑
        - duplicate columns, (email1, email2)
        - multipart columns "Joe Bega"
        - Multivalue columns ('cs50', "web26, "iOS10")
        - claculated columns
        - non-pk columns that depend on each other

#Relationship Goals 🧑‍🤝‍🧑

##Javascript quizzes table setup

    Quiz database
    [
        quiz_id: 1
        quiz_name: "Javascript_quiz"
        quiz_questions: [
            id: 0,
            quiz_id: 0,
            question_id: 0
        ]
        questions: [
            question_id: 0,  //local key
            question_text: "what is closure?",
        ]
        question_options: [
            id: 0,
            question_id: 0,
            option_id: 3,
        ]
        options: [
            option_id: 0,
            option_text: "what?",
      
        ]
    ]


    ZOO database
    [
            zoos: [
            zoo_id: 0, 
            zoo_name: 'san diego zoo'
            zoo_address: "200 zoo place"
        ]
            animals: [
                animal_id: 0,
                animal_name: "lucas"
                species_id: 0
        ]
            species: [
                species_id: 0,
                species_name: "jerryfish"
        ]
            zoo_animals: [
            zoo_id: 0,
            animal_id: 0
        ]

    ]

  
![img_6.png](img_6.png)
##Add to knex boilerplate style after seeds  
###this enables usage of foreign keys

     pool: { // needed to enable foreign keys in sqlite
      afterCreate: (conn, done) => {
        // runs after a connection is made to the sqlite engine
        conn.run('PRAGMA foreign_keys = ON', done); // turn on FK enforcement
      },
    },
 

