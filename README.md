# notes
## Redirect stderr and stdin to log
```
cmd 2>&1 > log   <-- nothing on screen

cmd 2>&1 | tee log <-- to log as well as screen
```
https://www.cyberciti.biz/faq/redirecting-stderr-to-stdout/

Redirecting the standard error (stderr) and stdout to file
Use the following syntax:
$ command-name &>file

OR
$ command > file-name 2>&1

Another useful example:
# find /usr/home -name .profile 2>&1 | more

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
