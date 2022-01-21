# SQL CRUD

An assignment to design relational database tables with particular applications in mind.

The contents of this file will be deleted and replaced with the content described in the [instructions](./instructions.md)

# FIRST PART
### Tables and import
CREATE TABLE restaurants (
id INTEGER,
Restaurants TEXT,
Category TEXT,
Neighborhood TEXT,
Price TEXT,
Opening_Time TEXT,
Closing_Time TEXT,
Average_Rating INTEGER,
Good_for_kids TEXT
);

CREATE TABLE reviews (
id INTEGER,
Client_Name TEXT,
Review TEXT
);

.mode csv
.separator ","
.headers on

.import restaurants.csv restaurants
DELETE FROM restaurants WHERE rowid in (select rowid FROM restaurants LIMIT 1);
(Delete header from the table row 1)

.import reviews.csv reviews
DELETE FROM reviews WHERE rowid in (select rowid FROM reviews LIMIT 1);
(Delete header from the table row 1)

### SQL Queries
1. select * from restaurants where price = "Cheap" and neighborhood = "Harlem";
2. select * from restaurants where category = "Italian" and average_rating>=3 order by average_rating desc; 
3. SELECT * from restaurants where strftime('%H:%M', 'now') >= Opening_Time and strftime('%H:%M', 'now') <= Closing_Time;
4. select restaurants.id, restaurants.Restaurants, reviews.Review from restaurants inner join reviews on restaurants.id=reviews.id;
   update reviews SET review = "Perfect, food was amazing, service was on fire 5/5" where id=984;
5. delete from restaurants where good_for_kids = "False";
6. select neighborhood, count(Restaurants) from restaurants group by neighborhood; 

# SECOND PART

CREATE TABLE users (
id INTEGER PRIMARY KEY,
username TEXT,
user_password TEXT,
email TEXT
);

CREATE TABLE posts (
from_id INTEGER,
to_id INTEGER,
Messages TEXT,
Sent_time TEXT,
Stories TEXT,
Posted_time TEXT,
Visibility INT
);

.mode csv
.separator ","
.headers on

.import users.csv users
(No need to delete first row)

.import posts.csv posts
(No need to delete first row)

### SQL Queries
1. INSERT INTO users (id,username,user_password,email) VALUES (1001,"almadiwka",'ewpapdwp',"almadiwka@gmail.com");
2. INSERT INTO posts (from_id,to_id,Messages,Sent_time,Stories,Posted_time,Visibility) VALUES (1001,2,'Hi! I'm Almadi',"2021-11-01 20:44:35","hey","2021-10-1 20:44:35",1);
3. INSERT INTO posts (from_id,Stories,Posted_time) VALUES (1002,"What's the plan for today?","2021-11-01 0:08:45");
4. select * from posts where visibility=1 order by sent_time DESC LIMIT 10;
   select * from posts where visibility=1 order by posted_time DESC LIMIT 10;
5. select * from posts where from_id=1001 and to_id=2 and visibility=1 order by sent_time DESC LIMIT 10;   
6. update posts set visibility=0 where (SELECT ROUND((JULIANDAY('now') - JULIANDAY(sent_time)) * 24) > 24);
   update posts set visibility=0 where (SELECT ROUND((JULIANDAY('now') - JULIANDAY(posted_time)) * 24) > 24);
7. select from_id, stories, sent_time, visibility from posts where visibility=0 order by sent_time DESC LIMIT 10;
   select from_id, stories, posted_time, visibility from posts where visibility=0 order by posted_time DESC LIMIT 10;
8. select posts.from_id, users.username, count(*) from posts inner join users on posts.from_id=users.id group by posts.from_id;
9. select posts.messages, users.email, users.username from posts inner join users on posts.from_id=users.id where (SELECT ROUND((JULIANDAY('now', '+8 hours') - JULIANDAY(sent_time)) * 24) <= 24);
10. select users.email from users left join posts on users.id=posts.from_id where posts.stories IS NULL;  
