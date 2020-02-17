# notes
## Redirect stderr and stdin to log
```
cmd 2>&1 > log   <-- nothing on screen

cmd 2>&1 | tee log <-- to log as well as screen
```

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
