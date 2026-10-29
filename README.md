# Recycling Management Database

A command-line CRUD application for a recycling company database. It is built with Python and MySQL and manages recycling materials, cities, branch offices, and the machines assigned to each branch. The project is a database coursework example; the interactive interface and SQL schema cover these four entities.

## Features

- Create, list, search, update, and delete records for materials, cities, branches, and machines.
- Check foreign-key relationships when adding or deleting related records.
- List the machines assigned to a branch (JOIN query).
- Find the branch that owns the most expensive machine (aggregation query).
- Load a sample dataset from the SQL script.

## Database Schema

The SQL script defines four tables:

- `materiais`: recycling status, color, and material type.
- `cidades`: city name, state, and size.
- `filiais`: branch contact and address details, with references to a city and a material.
- `maquinas`: machine details, purchase and last-revision dates, value, and a reference to a branch.

The relationships are represented by foreign keys: branches reference cities and materials, and machines reference branches. The SQL script also inserts and updates sample records and includes example JOIN and aggregate queries.

## Project Files

The application modules are in `Trabalho_BAN/projeto_reciclagem/`:

- `Principal.py`: interactive menu and database queries.
- `Conexao.py`: MySQL connection settings.
- `Cidades.py`, `Filiais.py`, `Materiais.py`, and `Maquinas.py`: operations for each entity.

The database setup and sample data are in `projeto_reciclagemdb.sql` at the repository root.

## Requirements

- Python 3
- MySQL Server
- The Python package `mysql-connector-python`

Install the connector with:

```bash
python -m pip install mysql-connector-python
```

## Setup and Run

1. Create the database:

	```sql
	CREATE DATABASE projeto_reciclagemDB;
	```

2. From the repository root, import the schema and sample data. For example, with the MySQL command-line client:

	```bash
	mysql -u root -p projeto_reciclagemDB < projeto_reciclagemdb.sql
	```

	The database must exist before importing the script.

3. Configure the MySQL host, username, password, and database in `Trabalho_BAN/projeto_reciclagem/Conexao.py`. The current file uses `localhost`, user `root`, password `1234`, and database `projeto_reciclagemDB`.

4. Start the application from its module directory:

	```bash
	cd Trabalho_BAN/projeto_reciclagem
	python Principal.py
	```

## Using the Menu

Choose an option to insert, update, search by ID, delete, or list records; run the JOIN or aggregation query; display all four tables; or exit. When prompted for a table, use `maquinas`, `filiais`, `materiais`, or `cidades`. Insert values as comma-separated input in the column order requested by the selected operation. The application prints query results and operation messages in the terminal.


