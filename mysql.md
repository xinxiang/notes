# GROUP_CONCAT
```
> select group_concat(column_name) from information_schema.columns where table_schema='utid' and table_name='hris_org' and column_name like 'unit_short%';
+--------------------------------------------------------------------------------------------------------------------------+
| group_concat(column_name)                                                                                                |
+--------------------------------------------------------------------------------------------------------------------------+
| unit_short1,unit_short2,unit_short3,unit_short4,unit_short5,unit_short6,unit_short7,unit_short8,unit_short9,unit_short10 |
+--------------------------------------------------------------------------------------------------------------------------+
1 row in set (0.00 sec)
```

group_concat() concatenates string values in different rows; while concat_ws() and concat() concatenate two or more string values in different columns.

group_concat() returns a single string, not a list of values; therefore, the result can not be used in IN operators.

**Ref:** https://www.mysqltutorial.org/mysql-group_concat/
