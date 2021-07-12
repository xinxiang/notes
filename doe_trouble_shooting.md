tapor server issues: networkservices@library.utoronto.ca

nightly_activities_uht
```
    echo "**** for only the updated corpus texts ****"
    /doe/corpus/scripts/corpuscheckin

*** validate and check in corpus ***
**** for only the updated corpus texts ****
/doe/corpus/xml-corpus/c.xml:165: element teiCorpus: validity error : Element teiCorpus content does not follow the DTD, expecting (teiHeader , (((facsimile | sourceDoc | fsdDecl)+ , (TEI | teiCorpus)*) | (TEI | teiCorpus)+)), got (teiHeader CDATA )
</teiCorpus>
            ^
```

discovered wrong xml:id
```
> /usr/bin/xmllint --valid --noout /doe/corpus/xml-corpus/corpus.xml
/doe/corpus/xml-corpus/T12151.xml:49: element s: validity error : ID T12151000200 already defined
...
/doe/corpus/xml-corpus/corpus.xml:639: element teiCorpus: validity error : Element teiCorpus content does not follow the DTD, expecting (teiHeader , (((facsimile | sourceDoc | fsdDecl)+ , (TEI | teiCorpus)*) | (TEI | teiCorpus)+)), got (teiHeader CDATA CDATA CDATA ....
</teiCorpus>
            ^
```

no error
```
> /usr/bin/xmllint --valid --noout /doe/corpus/xml-corpus/c.xml
```
