# Installation notes
* cd /tmp
* Go to the download page https://lucene.apache.org/solr/downloads.html
* Click on PGP and save it to solr.asc
* Click on **Binary** releases: solr-8.5.1.tgz (Source release does not have bin/start.jar)
* Copy the link address from one of the list
* wget --no-check-certificate https://...
* Verify the download
```
tar -xzvf solr-8.5.1.tgz
mv solr-8.5.1 /data1/
copy solr.doe.sh to /data1/solr-8.5.1/bin/
cd /data1/solr-8.5.1
mkdir server/trial
sudo cp -p server/solr/solr.xml server/trial/
cd server/trial
sudo mkdir oec ww wwt wc
cd /data1/
sudo chown -R solr:solr solr-8.5.1
```
# start
* lsof 4.78 (CentOS release 5.11 (Final)) does not support -sTCP:LISTEN (version 4.89 on Ubuntu 18.04.4 works fine)
```
...
lsof: unsupported TCP/TPI info selection: C
lsof: unsupported TCP/TPI info selection: P
lsof: unsupported TCP/TPI info selection: :
lsof: unsupported TCP/TPI info selection: L
...
lsof 4.78
...
```
* remove -sTCP:LISTEN for lsof
```
        #running=$(lsof -t -PniTCP:$SOLR_PORT -sTCP:LISTEN)
        running=$(lsof -t -PniTCP:$SOLR_PORT)
```

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
