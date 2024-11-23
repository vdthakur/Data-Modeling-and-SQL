# CINEMA Data Modeling with SQL

This repository contains scripts, schemas, and solutions for managing a cinema database. The goal is to create, populate, and query a relational database for a cinema industry scenario using MySQL.

---

## Database Schema

### Tables

1. **Movies**
   - **Attributes**:
     - `id` (INT, Primary Key)
     - `title` (VARCHAR)
     - `year` (INT)
     - `length` (INT)
     - `language` (VARCHAR)
   - **Description**: Stores movie details such as title, release year, duration, and language.

2. **Actors**
   - **Attributes**:
     - `id` (INT, Primary Key)
     - `name` (VARCHAR)
     - `gender` (VARCHAR)
   - **Description**: Stores actor details such as name and gender.

3. **ActIn**
   - **Attributes**:
     - `actor_id` (INT, Foreign Key → Actors.id)
     - `movie_id` (INT, Foreign Key → Movies.id)
   - **Description**: Many-to-many relationship between actors and movies.

4. **Directors**
   - **Attributes**:
     - `id` (INT, Primary Key)
     - `name` (VARCHAR)
     - `nationality` (VARCHAR)
   - **Description**: Stores director details such as name and nationality.

5. **DirectedBy**
   - **Attributes**:
     - `movie_id` (INT, Foreign Key → Movies.id)
     - `director_id` (INT, Foreign Key → Directors.id)
   - **Description**: Relationship between directors and movies they have directed.

---

## Setup Instructions

1. **Database Setup**
   - Create a database named `CINEMA`.

2. **Create Tables**
   - Define primary keys (PK), foreign keys (FK), and data types.
   - Add constraints such as `NOT NULL`, `UNIQUE`, or `ON DELETE CASCADE` where appropriate.

3. **Insert Sample Data**
   - Populate the database with sample data covering all scenarios (e.g., multiple actors per movie, movies with different languages).

-- Insert sample data into the Movies table
INSERT INTO Movies (id, title, year, length, language)
VALUES 
    (1, 'The Twilight Saga: Eclipse', 2010, 124, 'en'),
    (2, 'The Twilight Saga: New Moon', 2009, 130, 'en'),
    (3, 'La La Land', 2016, 128, 'en'),
    (4, 'Amélie', 2001, 122, 'fr'),
    (5, 'Parasite', 2019, 132, 'ko');

-- Insert sample data into the Actors table
INSERT INTO Actors (id, name, gender)
VALUES 
    (1, 'Kristen Stewart', 'female'),
    (2, 'Robert Pattinson', 'male'),
    (3, 'Emma Stone', 'female'),
    (4, 'Ryan Gosling', 'male'),
    (5, 'Audrey Tautou', 'female');

-- Insert sample data into the ActIn table
INSERT INTO ActIn (actor_id, movie_id)
VALUES 
    (1, 1), 
    (1, 2),
    (2, 1),
    (2, 2),
    (3, 3),
    (4, 3),
    (5, 4);

-- Insert sample data into the Directors table
INSERT INTO Directors (id, name, nationality)
VALUES 
    (1, 'Chris Weitz', 'American'),
    (2, 'Damien Chazelle', 'American'),
    (3, 'Jean-Pierre Jeunet', 'French'),
    (4, 'Bong Joon-ho', 'South Korean');

-- Insert sample data into the DirectedBy table
INSERT INTO DirectedBy (movie_id, director_id)
VALUES 
    (1, 1),
    (2, 1),
    (3, 2),
    (4, 3),
    (5, 4);

---

## Queries

### SQL Questions

1. **Find titles of the longest movies.**
2. **Find titles of movies containing "Twilight" directed by "Steven Spielberg".**
3. **Find how many movies "Tom Hanks" has acted in.**
4. **Find directors who directed only one movie.**
5. **Find titles of movies with the largest number of actors.**
6. **Find names of actors who acted in both English (`language = "en"`) and French (`language = "fr"`) movies.**
7. **Find names of directors who only directed English movies.**

---

## Python Program

### `search.py`

- **Description**: A Python program that accepts an actor's name as input and returns titles of movies the actor has acted in.
- **Requirements**:
  - Query only the necessary data (avoid fetching entire tables).
  - Use parameterized queries to prevent SQL injection.

---
