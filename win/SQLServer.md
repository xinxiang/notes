# SQL Server
## select
```
select top(3) * from fim_id_preferred_prod;

select top(3) with ties * from fim_id_preferred_prod;

select top(3) percent * from fim_id_preferred_prod;

ORDER BY column_list [ASC |DESC]
OFFSET offset_row_count {ROW | ROWS}
FETCH {FIRST | NEXT} fetch_row_count {ROW | ROWS} ONLY
```
* https://database.guide/limit-the-rows-returned-in-a-sql-server-query-top-clause/
* http://www.sqlservertutorial.net/sql-server-basics/sql-server-offset-fetch/

## compare
* [Diff](https://www.mssqltips.com/sqlservertip/2779/ways-to-compare-and-find-differences-for-sql-server-tables-and-data/)
