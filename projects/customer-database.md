---
layout: project
type: project
image: img/customer-database/money-icon.jpg
title: "Simple bank customer database"
date: 2022-10-29
published: false
labels:
  - C
  - Database
summary: "Creating a simple customer database for my ICS 212 class."
---

<img class="img-fluid" src="../img/customer-database/database-header.jpg" alt="Laptop with a plant next to it.">

This project had us create a simple customer database for a bank that allows the banker to manage customer's bank records. The banker's tasks include creating new records, viewing an existing one, and deleting records. Records include the customer's account number, name, and address. There were two parts that we had to complete: The user interface and the database. The user interface had to be easy to work with since the banker is interacting with it and the database end had to include the following functions:

```
void addRecord(struct record **, int, char [ ], char [ ]); //Creates records and keeps the list in descending order of account numbers.
void printAllRecords(struct record *); //Prints all the records in the database.
int findRecord(struct record *, int); //Finds a record using the account number.
int deleteRecord(struct record **, int); //Deletes a record using the account number.
int writefile(struct record *, char []); //Saves all the records in the database to a file.
int readfile(struct record **, char []); //Retrieves the records from the saved file.
void cleanup(struct record **); //Releases all allocated spaces in the heap memory.
```

My role in this project was to create the user interface and database. Everything was written by me with the help of the professor, the teaching assistant, and online resources.

This experience had taught me the importance of pseudocoding. Before this class, I almost never used pseudocoding to plan out my programs and looking back on that, it really could have saved me a lot of time if I had just taken the time to write out my program and how it was going to be structured. As for this project, I pseudocoded all the functions before implementing it and it made my life as a programmer so much easier! Another thing I have learned from this experience was the importance of tracing out your program line by line and seeing how it interacts with the stack and heap memory for comprehension and debugging purposes. If I encountered any problem with my code, I would immediately start tracing out my code line by line in order to see where my logic went wrong and this also saved me a lot of time in the long run because I actively spent my time understanding what each line of code did rather than stare at my program for hours on end and wonder where I went wrong.
