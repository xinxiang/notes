# copyField - different types of source and dest fields
**Error**: Indexing failed
>> "msg":"ERROR: [doc=T200301] Error adding field 'id'='T200301' msg=For input string: \"T200301\"",
    "code":400}}

**Cause**: The id field was copied to a pint type field in manged-schema.
```
 <field name="id" type="string" multiValued="false" indexed="true" required="true" stored="false"/>
...
 <field name="sp_sort" type="pint" multiValued="false" indexed="true" stored="true"/>
 ...
 <copyField source="id" dest="sp_sort"/>
```
