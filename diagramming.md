# Diagramming Conventions in ERD

Entity Relationship Diagrams (ERDs) are the standard way to represent relational data. The most common representation is called the _crow's foot diagram_, for reasons that will become obvious!

ERDs use a boxes-and-lines approach to represent _entities_ of data and the relations between them.

## What is an entity?

This rather vaguely named beast refers to anything we can identify as having something knowable about it. A user. A person. A used car advert. A banking transaction.

Pretty much anything that has its own identity and we want to work with some information about it.

In our relational database, an entity becomes a _row_ of a _table_.

## Tables

Tables are represented by a box.

The box has a heading bar. The name of the table goes inside that header bar. This is the name we have given to one of our entities - those interesting things we wish to store information about.

In the image below, we have a table to represent `user`s of our system. The table name is user. You'll also see something in the box below - a column, which we'll describe next.

Here is our table as an ERD:

![Image of a table. It has a heading bar at the top with the name of the table, in this case "user". Below that is a box, containing the one column we have and the column name, in this case 'name' of the user](/images/table-1-col.png)

## Columns

The table above had a single column, called name. Let's add a couple more:

![Same user table with two more columns called email and birthdate added](/images/table-3-cols.png)

We have three columns in total, each one some information about an individual `user` - their name, email and birth date.

ERDs represent a column with a **column name** and a **data type**.

The `birthdate` column has a data type of `datetime`. Most relational databases have something like a `datetime` type to work with time and date information.

### Rows - never shown

Just a note on rows: ERDs show the _schema_ of the database, not its actual _content_. As such, we never diagram individual rows.

## Primary Key

Tables will generally have a _primary key_, used to uniquely identify a single row in the table.

Let's add a surrogate primary key of `user_id` into our `user` table.

Primary keys are repesented as a column in our ERD, but are highlighted to show their importance:

![Primary key column user_id is shown in bold with a small padlock icon](/images/table-primary-key.png)

We see the column is highlighted in bold, and there is a small padlock icon shown.

## One to one relation

Let's give our `User` a profile page. We create a table `Profile` to store their mugshot as a URL, and a lengthy description of their (self-penned) grandiose achievements.

Each user has one and only one profile, making this a one-to-one relationship.

We model this using a _line_ joining the column in `User` that references the profile (`profile_fk`) to the primary key of the linked profile (`profile_id`) in the `Profile` table:

![Showing one to one link between user and profile](/images/one-to-one.png)

> Be specific: the line should align with the actual PK and FK on the diagram

Notice the details on the line:

- Each end is labelled with a digit '1'
- The line has a short single stroke crossing through at each end

These details show the _cardinality_ of the relation: one to one.

![Crow versus crow's feet](/images/crows-feet-crow.jpg)

## One to many relation

Let's add a `Post` table to hold the overflowing wit and wisdom of our `User`. It will store the text of their writing plus the date and time when it was posted:

![Image linking one User to many Post entities](/images/one-to-many.png)

One `user` may write many `Post`s

The diagram features a link connecting the foreign key `user_fk` of the `Post` entity back to the `user_id` primary key of the `User`.

The link graphic features:

- A single short stroke at the 'User' end
- A _crow's foot_ symbol (htree lines fanning out from a point) at `Post`

This is a one to many relationship when viewed starting from 'User'. It is equally a many-to-one relationship when viewed starting from `Post`.

## Many to many - link table

Many to many links can simply be two tables linked by a line with crow's feet at each end.

It is common to use a different approach that intoduces a thirs table. This is known as a _link table_. Each row links together rows from two other tables.

Let's introduce a feature for a User to complain about a `Post`.

This is a many-to-many relationship ebtween `user` and `post`:

- One `user` can raise complaints about many posts
- One `Post` can be the subject of complaints by many users

Using a link table called `Complaint` to represent this many-to-many relationship, the ERD looks like this:

![Image of table linking User to Post ](/images/many-to-many.png)

We've added some columns into the link table `Complaint` which are `link attributes`.

These are attributes belonging to the link itself - the complaint. In our case, this is the date the complaint was created, stored in column `created` as a `datetime` type.

# Next

[Exercise](/exercise.md)

[Back to Contents](/contents.md)
