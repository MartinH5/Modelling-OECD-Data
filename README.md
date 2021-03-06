# Modelling-OECD-Data


## 1. Logical Model

I setup each entity with their own primary key (being their ID) as well as their respective values. As well as an entity that has a reference to each and all of them (referencing their primary key).

![Logical Model](https://raw.githubusercontent.com/MartinH5/Modelling-OECD-Data/master/Untitled%20Diagram%20(1).png)

![alt text](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 1")


## 2. SQL 

First we need to create all the seperate entities from the model in psql: 

```
Create Table measure(id serial primary key, measure varchar(100) unique);
Create Table subject(id serial primary key, subject varchar(100) unique);
Create Table flag(id serial primary key, flag varchar(100) unique);
Create Table frequency(id serial primary key, frequency varchar(100) unique);
Create Table location(id serial primary key, location varchar(100) unique);
Create Table indicator(id indicator primary key, indicator varchar(100) unique);
```

Then we gather them under one table:

``` 
Create Table value(id serial primary key, value numeric, 
                   measureID int references measure(id),
                   subjectID int references subject(id),
                   flagID int references flag(id),
                   frequencyID int references frequency(id),
                   locationID int references location(id),
                   indicator int references indicator(id),
                   timeID int references time(id));
``` 

I unforunately struggled to establish a connection to my database - using python's psycopg2 and got stuck. 



