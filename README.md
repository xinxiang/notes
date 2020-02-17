# notes
## Timing times elapsed
* with time command
```
/usr/bin/time -p -ao ../log/updateoec.log ./updateoec 0 &> ../log/updateoec.log
```
* within script
```
  my $sttime = time;
  ...
  print "Elapsed time : ", time - $sttime, " seconds\n";

```
