[![Travis Build Badge](https://travis-ci.org/magicalbanana/npq.svg?branch=master)](https://travis-ci.org/magicalbanana/npq)
[![Coveralls Coverage Badge](https://coveralls.io/repos/github/magicalbanana/npq/badge.svg?branch=master)](https://coveralls.io/github/magicalbanana/npq?branch=master)
[![RTD Documentation Badge](https://readthedocs.org/projects/npq/badge/?version=latest)](http://npq.readthedocs.io/en/latest/?badge=latest)
[![GoDoc](https://godoc.org/github.com/magicalbanana/npq?status.svg)](https://godoc.org/github.com/magicalbanana/npq)

# SQLTMPL - SQL Template

Allows the named parameters found in a SQL statement to be replaced with positional parameters.

Example:

before:
```go
query := NewNamedParameterQuery("
    SELECT * FROM table
    WHERE col1 = :foo
    AND col2 IN(:first_name, :middle_name, :last_name)
")

query.SetValue("foo", "bar")
query.SetValue("first_name", "Alice")
query.SetValue("last_name", "Bob")
query.SetValue("middle_name", "Eve")

connection, _ := sql.Open("postgres", "user:pass@tcp(localhost:3306)/db")
connection.QueryRow(query.GetParsedQuery(), (query.GetParsedParameters())...)
```

after
```sql
SELECT * FROM boo AS b WHERE b.moo = ?
```

## USAGE
