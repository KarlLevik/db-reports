# Database reporting scripts

## Features

- Reads config files
- Can read command-line arguments
- Runs SQL statements/queries and can get a result set
- Can writes the result set to a spreadsheet file (.xlsx or .csv)
- Can email the spreadsheet as an attachment, or just a path name, if recipient email addresses are defined in the config file.

## Installing dependencies

```bash
pip install --user XlsxWriter
pip install --user python-tds
pip install --user mysql-connector
pip install --user psycopg2
```
`python-tds` is a connector for Microsoft SQL Server, `mysql-connector` is a connector that works with MySQL and MariaDB, and `psycopg2` is a connector for PostgreSQL.

You only need the database connector(s) for the database system type(s) that you intend to use.

## Configuration

Copy the files `*.example.cfg` files to just `*.cfg`:

 * `config.example.cfg` to `config.cfg`
 * `jobs.example.cfg` to `jobs.cfg`
 * `datasources.example.cfg` to `datasources.cfg`

Then customise them to use your own database credentials, database queries and email settings.

## Example usage

```bash
# Report on plates and imagings from a RockMaker database
python runreport.py RockMakerPlateReport month 2018 10
# Report on plates and imagings from an ISPyB database
python runreport.py ISPyBPlatesReport month 2018 09
```

## Developing new reports

You will need to add this to the 'jobs.cfg' file:
- An SQL template string for your database query
- A list with the column headers you want to use in the report

You also need to add database credentials to the `datasources.cfg` file and email settings to the `config.cfg` file.

If your database system is not yet supported, then you need to amend the `create_report` in the `DBReport` class.

See also the *.example.cfg files for examples.
