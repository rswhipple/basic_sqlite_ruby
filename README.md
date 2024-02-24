# basic_sqlite_ruby

## Description

This project reconstructs SQLite's basic functionality from scratch in Ruby. It supports CRUD operations through a custom API.

**MySqliteRequest Class**: Found in `my_sqlite_request.rb`, this class mimics SQLite's functionality, allowing queries to be built through method chaining and executed with the `.run` method. Each record requires an ID, with support for one join and one where clause per query.
  
**Command Line Interface (CLI)**: Uses the `readline` library and a modular parsing system to interpret queries, executable with `ruby my_sqlite_cli.rb`. The CLI supports:
  - SELECT|INSERT|UPDATE|DELETE with up to one WHERE condition.
  - JOIN operations with up to one ON condition.

The project uses CSV files as a database, making it easy to work with data using Ruby's CSV library.

## Installation

Before running the project, make sure Ruby is installed on your system. If Ruby is not installed, visit [the official Ruby website](https://www.ruby-lang.org/en/downloads/) for installation instructions.

## Usage

To start the CLI, run:
```bash
ruby my_sqlite_cli.rb
```

Example queries:
```sql
SELECT * FROM nba_player_data.csv;
SELECT name, age FROM nba_player_data.csv;
SELECT name, birth_city FROM nba_player_data.csv JOIN nba_players.csv ON name=Player;
INSERT INTO nba_player_data.csv VALUES (name, year_start, year_end, position, height, weight, birth_date, college);
UPDATE nba_player_data.csv SET name = 'Updated Name', year_start = '99' WHERE name = 'Original Name';
DELETE FROM nba_player_data.csv WHERE name = 'Updated Name';
```

## Running Tests

For testing, execute:
```bash
ruby my_sqlite_request_test.rb && TEST=true ruby my_sqlite_cli_test.rb
```
The tests are structured to comprehensively cover the variety of request types, featuring 13 tests and 27 assertions.

## The Core Team
Made collaboratively by:
Mathius Johnson and Rebecca Whipple Silverstein

