# World Cup Database Project

## Project Overview

This project requires you to create a database to store match data from the final three rounds of the World Cup since 2014, using the `games.csv` file as the data source. The CSV file contains a comma-separated list of matches, including the year, round, winner, opponent, winner goals, and opponent goals. The project consists of three main parts: creating the database, inserting data, and querying the database to produce output matching `expected_output.txt`.

## Part 1: Creating the Database

Log into the psql interactive terminal using `psql --username=freecodecamp --dbname=postgres`. Create a database named `worldcup` and connect to it with `\c worldcup`. Create two tables: `teams` with columns `team_id` (SERIAL, primary key) and `name` (VARCHAR, UNIQUE, NOT NULL), and `games` with columns `game_id` (SERIAL, primary key), `year` (INT, NOT NULL), `round` (VARCHAR, NOT NULL), `winner_id` (INTEGER, foreign key to `team_id`, NOT NULL), `opponent_id` (INTEGER, foreign key to `team_id`, NOT NULL), `winner_goals` (INT, NOT NULL), and `opponent_goals` (INT, NOT NULL).

## Part 2: Inserting Data

Complete the `insert_data.sh` script to insert data from `games.csv` into the database. Do not modify the initial code in the script. Use the `PSQL` variable for queries, e.g., `$($PSQL "<query_here>")`. The script must insert 24 unique teams from the `winner` and `opponent` columns into the `teams` table and 32 match rows (excluding the header) into the `games` table, with correct `winner_id` and `opponent_id` referencing `team_id`. Optimize the script for efficiency, as tests have a 20-second limit. To clear tables, use `TRUNCATE TABLE games, teams;`.

## Part 3: Querying the Database

Complete the empty `echo` commands in `queries.sh` to produce output matching `expected_output.txt`. Use the `PSQL` variable for queries. The first query is provided as an example; complete the rest in a single line each. Ensure the database is populated correctly from `insert_data.sh` for accurate results. Test queries in the psql prompt before adding them to the script. The output must exactly match `expected_output.txt`, including decimal precision.

## Additional Notes

- **File Permissions**: Ensure `insert_data.sh` and `queries.sh` have executable permissions with `chmod +x insert_data.sh queries.sh`. Tests will fail without these permissions and may take longer to run.
- **Database Backup**: Save your database to avoid data loss by running `pg_dump -cC --inserts -U freecodecamp worldcup > worldcup.sql`. Restore it with `psql -U postgres < worldcup.sql`. The dump file is saved where the command is executed.
- **Project Submission**: After passing all tests, save `worldcup.sql`, `insert_data.sh`, and `queries.sh` in a public repository and submit the repository URL to freeCodeCamp.org.
- **games.csv Structure**: The file contains match data with columns: `year`, `round`, `winner`, `opponent`, `winner_goals`, and `opponent_goals`.
