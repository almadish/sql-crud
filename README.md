# SQL CRUD Training

Complete the following exercises. For each:

- determine the structure of any tables
- determine the data type of any fields
- determine which field(s) is the primary key for each table
- determine which field(s) is the foreign keys for any tables that require them
- write SQL queries that perform the requested functionality.

## Part 1: Restaurant finder

Design a database table named `restaurants` that would allow an application that uses it to find restaurants and a table named `reviews` that would hold reviews for any restaurant.

### Table structure

Decide what fields and data types are necessary for the `restaurants` table. Bear in mind that the application must be able to filter restaurants by...

- **Category** (i.e. genre of food)
- **Price tier** (i.e cheap, medium, or expensive)
- **Neighborhood** (a particular NYC neighborhood)
- **Opening hours** (for simplicity, you can assume each restaurant has the same opening hours every day)
- **Average rating** (out of 5 stars)
- **Good for kids** (true or false)

The application must also be able to allow users to leave reviews associated with any restaurant.

Write the SQL commands to create the tables with the structure you determine is necessary.

### Practice data

Insert realistic-looking dummy data for one thousand restaurants. Use [mockaroo.com](https://mockaroo.com) - a tool for generating mock data - helpful. A few non-obvious notes about Mockaroo:

- Mockaroo's **Row Number** field type can be used to generate primary key numbers.
- Mockaroo's **Time** field type can generate times in 24 hour format which is useful for generating opening/closing times necessary for restaurant data in this assignment.
- Mockaroo's **Custom List** field type can randomly pick from a list of values you enter. This can be useful for randomly picking from a set of NYC neighborhood names for any restaurant.

Include the practice data in a CSV file named `restaurants.csv` in the directory named `data`.

Write the SQLite commands necessary to import the data.

### Queries

Write a single SQL query to perform each of the following tasks:

1. Find all cheap restaurants in a particular neighborhood (pick any neighborhood as an example).

1. Find all restaurants in a particular genre (pick any genre as an example) with 3 stars or more, ordered by the number of stars in descending order.

1. Find all restaurants that are open now (see hint below).

1. Leave a review for a restaurant (pick any restaurant as an example).

1. Delete all restaurants that are not good for kids.

1. Find the number of restaurants in each NYC neighborhood.

## Part 2: Social media app

The social media app you are designing a database for allows Users to share two kinds of content: **Messages** and **Stories**.

### Tables structure

Decide what fields and data types are necessary for the two tables necessary for this app: `users` and `posts`. The `posts` table stores both Messages and Stories.

Bear in mind that the application must be able to use these tables to perform the required functionality outlined below.

#### Users:

Users can register for the app by supplying their...

- email
- password
- handle (i.e. username).

#### Messages:

- Messages consist of text only.
- Messages are sent from one user to another specific user.
- Messages become invisible immediately after view and don't show up in the app thereafter.
- Messages are never actually deleted from the database table, even when invisible to the user (the social media company that produces the app keeps 'deleted' content in its database for future data harvesting, monetization purposes, and more.)

#### Stories:

- Stories consist of text only.
- Stories are public and every user can see them.
- Stories become invisible 24 hours after posting and don't show up in the app thereafter.
- Stories are never deleted from the database table, even when invisible to the user.

Write the SQL command to create these tables with the structure you determine is necessary.

### Practice data

Insert realistic-looking dummy data for one thousand Users, one thousand Messages, and one thousand Stories.

Include the practice data in CSV files named `users.csv` and `posts.csv` in the directory named `data`.

Write the SQLite commands necessary to import the data into the respective tables.

### Queries

Write a single SQL query to perform each of the followin tasks:

1. Register a new User.

1. Create a new Message sent by a particular User to a particular User (pick any two Users for example).

1. Create a new Story by a particular User (pick any User for example).

1. Show the 10 most recent visible Messages and Stories, in order of recency.

1. Show the 10 most recent visible Messages sent by a particular User to a particular User (pick any two Users for example), in order of recency.

1. Make all Stories that are more than 24 hours old invisible.

1. Show all invisible Messages and Stories, in order of recency.

1. Show the number of posts by each User.

1. Show the post text and email address of all posts and the User who made them within the last 24 hours.

1. Show the email addresses of all Users who have not posted anything yet.
