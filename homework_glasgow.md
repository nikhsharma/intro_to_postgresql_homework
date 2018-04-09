# SQL Homework

The Glasgow Film Theatre are having a Marvel Movie Marathon! They have asked you to help maintain their database of movies with times and attendees.

## To access the database:

First, create a database called 'marvel'
```
# terminal
createdb marvel
```

Next, run the provided SQL script to populate your database:
```
# terminal
psql -d marvel -f marvel.sql
```

Use the supplied data as the source of data to answer the questions.  Copy the SQL command you have used to get the answer, and paste it below the question, along with the result they gave.

## Questions

1. Return ALL the data in the 'movies' table.


marvel=# SELECT * FROM movies;
 id |                title                | year | show_time
----+-------------------------------------+------+-----------
  1 | Iron Man                            | 2008 | 21:55
  2 | The Incredible Hulk                 | 2008 | 15:45
  3 | Iron Man 2                          | 2010 | 18:30
  4 | Thor                                | 2011 | 13:00
  5 | Captain America: The First Avenger  | 2011 | 23:45
  6 | Avengers Assemble                   | 2012 | 16:50
  7 | Iron Man 3                          | 2013 | 16:35
  8 | Thor: The Dark World                | 2013 | 21:55
  9 | Batman Begins                       | 2005 | 17:30
 10 | Captain America: The Winter Soldier | 2014 | 15:30
 11 | Guardians of the Galaxy             | 2014 | 15:30
 12 | Avengers: Age of Ultron             | 2015 | 13:30
 13 | Ant-Man                             | 2015 | 19:25
 14 | Captain America: Civil War          | 2016 | 16:50
 15 | Doctor Strange                      | 2016 | 22:10
 16 | Guardians of the Galaxy 2           | 2017 | 16:30
(16 rows)



2. Return ONLY the name column from the 'people' table

marvel=# SELECT name FROM people;
       name       
------------------
 Sarah Bartlett
 Kelsie Braidwood
 Liam Kavenns
 Daniel Childs
 Victor Chugbo
 Brian Cooke
 Patrick Cullen
 Roberto De Marco
 Ruaridh Dunbar
 Edward Fallon
 Hadsan Geele
 Paul Kelly
 John McCollum
 Andrew Lowrie
 Callum Mackenzie
 Chris Marshall
 Fraser McKay
 Lyle Mitchell
 Stuart O'Donnell
 Connor Rose
 Nikhil Sharma
 Scott Stevenson
(22 rows)

3. Oops! Someone at CodeClan spelled Liam's name wrong! Change it to reflect the proper spelling ('Liam Kavenns' should be 'Liam Cavens').

marvel=# UPDATE people SET name = 'Liam Cavens' WHERE name = 'Liam Kavenns';
UPDATE 1
marvel=# SELECT name FROM people;
       name       
------------------
 Sarah Bartlett
 Kelsie Braidwood
 Daniel Childs
 Victor Chugbo
 Brian Cooke
 Patrick Cullen
 Roberto De Marco
 Ruaridh Dunbar
 Edward Fallon
 Hadsan Geele
 Paul Kelly
 John McCollum
 Andrew Lowrie
 Callum Mackenzie
 Chris Marshall
 Fraser McKay
 Lyle Mitchell
 Stuart O'Donnell
 Connor Rose
 Nikhil Sharma
 Scott Stevenson
 Liam Cavens
(22 rows)

4. Return ONLY your name from the 'people' table.

marvel=# SELECT name FROM people WHERE name = 'Nikhil Sharma';
     name      
---------------
 Nikhil Sharma
(1 row)

5. The cinema is showing 'Batman Begins', but Batman is DC, not Marvel! Delete the entry from the 'movies' table.

marvel=# DELETE FROM movies WHERE title = 'Batman Begins';
DELETE 1
marvel=# SELECT title FROM movies;
                title                
-------------------------------------
 Iron Man
 The Incredible Hulk
 Iron Man 2
 Thor
 Captain America: The First Avenger
 Avengers Assemble
 Iron Man 3
 Thor: The Dark World
 Captain America: The Winter Soldier
 Guardians of the Galaxy
 Avengers: Age of Ultron
 Ant-Man
 Captain America: Civil War
 Doctor Strange
 Guardians of the Galaxy 2
(15 rows)

6. Create a new entry in the 'people' table with the name of one of the instructors.

marvel=# INSERT INTO people (name) VALUES ('Alan Russell');
INSERT 0 1
marvel=# SELECT * FROM people;
 id |       name       
----+------------------
  1 | Sarah Bartlett
  2 | Kelsie Braidwood
  4 | Daniel Childs
  5 | Victor Chugbo
  6 | Brian Cooke
  7 | Patrick Cullen
  8 | Roberto De Marco
  9 | Ruaridh Dunbar
 10 | Edward Fallon
 11 | Hadsan Geele
 12 | Paul Kelly
 13 | John McCollum
 14 | Andrew Lowrie
 15 | Callum Mackenzie
 16 | Chris Marshall
 17 | Fraser McKay
 18 | Lyle Mitchell
 19 | Stuart O'Donnell
 20 | Connor Rose
 21 | Nikhil Sharma
 22 | Scott Stevenson
  3 | Liam Cavens
 23 | Alan Russell
(23 rows)

7. John McCollum has decided to hijack our movie evening, Remove him from the table of people.

marvel=# DELETE FROM people WHERE name = 'John McCollum';
DELETE 1
marvel=# SELECT * FROM people;
 id |       name       
----+------------------
  1 | Sarah Bartlett
  2 | Kelsie Braidwood
  4 | Daniel Childs
  5 | Victor Chugbo
  6 | Brian Cooke
  7 | Patrick Cullen
  8 | Roberto De Marco
  9 | Ruaridh Dunbar
 10 | Edward Fallon
 11 | Hadsan Geele
 12 | Paul Kelly
 14 | Andrew Lowrie
 15 | Callum Mackenzie
 16 | Chris Marshall
 17 | Fraser McKay
 18 | Lyle Mitchell
 19 | Stuart O'Donnell
 20 | Connor Rose
 21 | Nikhil Sharma
 22 | Scott Stevenson
  3 | Liam Cavens
 23 | Alan Russell
(22 rows)

8. The cinema has just heard that they will be holding an exclusive midnight showing of 'Spider-man: Homecoming'!! Create a new entry in the 'movies' table to reflect this.

marvel=# INSERT INTO movies (title, year, show_time) VALUES ('Spider-man: Homecoming', 2018, '00:00');
INSERT 0 1
marvel=# SELECT * FROM movies;
 id |                title                | year | show_time
----+-------------------------------------+------+-----------
  1 | Iron Man                            | 2008 | 21:55
  2 | The Incredible Hulk                 | 2008 | 15:45
  3 | Iron Man 2                          | 2010 | 18:30
  4 | Thor                                | 2011 | 13:00
  5 | Captain America: The First Avenger  | 2011 | 23:45
  6 | Avengers Assemble                   | 2012 | 16:50
  7 | Iron Man 3                          | 2013 | 16:35
  8 | Thor: The Dark World                | 2013 | 21:55
 10 | Captain America: The Winter Soldier | 2014 | 15:30
 11 | Guardians of the Galaxy             | 2014 | 15:30
 12 | Avengers: Age of Ultron             | 2015 | 13:30
 13 | Ant-Man                             | 2015 | 19:25
 14 | Captain America: Civil War          | 2016 | 16:50
 15 | Doctor Strange                      | 2016 | 22:10
 16 | Guardians of the Galaxy 2           | 2017 | 16:30
 17 | Spider-man: Homecoming              | 2018 | 00:00
(16 rows)

9. The cinema would also like to make the Guardian movies a back to back feature. Update the 'Guardians of the Galaxy' show time from 15:30 to 21:00, and the 'Guardians of the Galaxy 2' show time from '16:30' to '22:00'.

marvel=# UPDATE movies SET show_time = '21:00' WHERE id = 11;
UPDATE 1
marvel=# UPDATE movies SET show_time = '22:00' WHERE id = 16;
UPDATE 1
marvel=# SELECT * FROM movies;                   
 id |                title                | year | show_time
----+-------------------------------------+------+-----------
  1 | Iron Man                            | 2008 | 21:55
  2 | The Incredible Hulk                 | 2008 | 15:45
  3 | Iron Man 2                          | 2010 | 18:30
  4 | Thor                                | 2011 | 13:00
  5 | Captain America: The First Avenger  | 2011 | 23:45
  6 | Avengers Assemble                   | 2012 | 16:50
  7 | Iron Man 3                          | 2013 | 16:35
  8 | Thor: The Dark World                | 2013 | 21:55
 10 | Captain America: The Winter Soldier | 2014 | 15:30
 12 | Avengers: Age of Ultron             | 2015 | 13:30
 13 | Ant-Man                             | 2015 | 19:25
 14 | Captain America: Civil War          | 2016 | 16:50
 15 | Doctor Strange                      | 2016 | 22:10
 17 | Spider-man: Homecoming              | 2018 | 00:00
 11 | Guardians of the Galaxy             | 2014 | 21:00
 16 | Guardians of the Galaxy 2           | 2017 | 22:00
(16 rows)


## Extension

1. Research how to delete multiple entries from your table in a single command.
marvel=# DELETE FROM movies WHERE id BETWEEN 1 AND 4;
DELETE 4
marvel=# SELECT * FROM movies;
 id |                title                | year | show_time
----+-------------------------------------+------+-----------
  5 | Captain America: The First Avenger  | 2011 | 23:45
  6 | Avengers Assemble                   | 2012 | 16:50
  7 | Iron Man 3                          | 2013 | 16:35
  8 | Thor: The Dark World                | 2013 | 21:55
 10 | Captain America: The Winter Soldier | 2014 | 15:30
 12 | Avengers: Age of Ultron             | 2015 | 13:30
 13 | Ant-Man                             | 2015 | 19:25
 14 | Captain America: Civil War          | 2016 | 16:50
 15 | Doctor Strange                      | 2016 | 22:10
 17 | Spider-man: Homecoming              | 2018 | 00:00
 11 | Guardians of the Galaxy             | 2014 | 21:00
 16 | Guardians of the Galaxy 2           | 2017 | 22:00
(12 rows)
