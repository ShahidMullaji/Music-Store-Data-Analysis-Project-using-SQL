# Music-Store-Data-Analysis-Project-using-SQL

# Online Music Store SQL Analysis

## About the Project

This is a SQL project I did on an online music store database (similar to the Chinook database).It has data about customers, employees, invoices, tracks, albums, artists, and genres. I wrote queries to answer some common business questions that a company like this might actually ask.

## Objective

I wanted to practice writing SQL queries that go beyond basic SELECT statements  using joins across multiple tables, grouping data, and using subqueries to answer specific business questions instead of just pulling raw data.

## Tools Used

- PostgreSQL
- SQL (Joins, Group By, Subqueries, Aggregate Functions)

## Dataset

The database has these tables:

- customer
- employee
- invoice
- invoice_line
- track
 - album
- artist
- genre
- media_type
- playlist
- playlist_track

Important columns I used across the queries: 'customer_id', 'first_name', 'last_name', 'email', 'billing_country', 'billing_city', 'total', 'unit_price', 'quantity', 'genre_id', 'artist_id', 'album_id', 'milliseconds', and 'levels' (for employee seniority).

## Analysis

Here are the questions I answered with SQL in this project:

1. Who is the most senior employee based on job level?
2. Which country has the most invoices?
3. What are the top 3 highest invoice totals?
4. Which city has generated the most revenue overall (useful for deciding where to hold a promotional music festival)?
5. Who is the best customer, based on total amount spent?
6. Which customers listen to Rock music? Returned their first name, last name, and email, sorted alphabetically by email.
7. Which 10 artists have the most Rock tracks in the catalog?
8. Which tracks are longer than the average track length?
9. How much has each customer spent, broken down by artist?

## Key Insights

- The query in Q4 shows which city brings in the most total invoice revenue — this is the kind of thing that would help decide where to run a promotional event.
- The "best customer" query ranks customers by total spend, so the top row is the highest-paying customer.
- For the artist spend query, I had to use `unit_price * quantity` from `invoice_line` instead of the invoice's total amount. Using the invoice total would have counted the same invoice multiple times if it had tracks from different artists, which would give a wrong number.
- The Rock genre queries show that filtering through `genre_id` and joining it all the way up to `artist` needs quite a few joins (track → genre, track → album → artist), so getting the join order and keys right mattered a lot.

## Project Structure

```
onlinemusic.sql
```

All the queries for this project are in the single `onlinemusic.sql` file, with comments above each query explaining what business question it answers.

## How to Run

1. Set up a PostgreSQL database with the online music store schema (customer, invoice, track, artist, genre, etc.).
2. Open `onlinemusic.sql` in pgAdmin or any PostgreSQL client.
3. Run the queries one by one — each one is separated and commented with the question it's answering.

## What I Learned

- How to join multiple tables correctly to trace a relationship (like going from a track all the way to its artist through album and genre).
- The difference between using `invoice.total` and calculating the actual amount from `invoice_line.unit_price * quantity` — and why it matters when you're grouping by something other than the invoice itself.
- Using `GROUP BY` with aggregate functions like `SUM`, `COUNT`, and `AVG` to answer specific questions instead of just summarizing everything.
- Using a subquery to compare each row against an average value (used this for finding tracks longer than the average song length).

## Author

Mohammad Shahid
