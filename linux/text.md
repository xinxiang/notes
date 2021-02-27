* [Find the number of tabs in each line](https://stackoverflow.com/questions/15517363/how-to-count-number-of-tabs-in-each-line-using-shell-script)
```
awk '{print gsub(/\t/, "")}' infile
```
* Get the 12th line from a file
```
sed -n '12 p' infile
```

* Count the number of characters of each line in a file
```
while IFS= read -r line; do echo $(( ${#line} + 1 )); done < infile
```

* [Replace by position](https://www.unix.com/shell-programming-and-scripting/175977-awk-command-replace-specific-position-characters.html) - replace col 306 to 386 with placeholder@gmail.com and fill the reset with space:
```
awk 'function repl(s,f,t,v)
{return substr(s,1,f-1) sprintf("%-*s", t-f+1, v) substr(s,t+1)}
{a=repl($0,306,386,"placeholder@gmail.com")
print a}' srcFile > outFile

```
* Find and Update Content with perl
```
find . type f -name Root | xargs perl -pie "s/\/home\/doe\//\/data\//"
Can't open perl script "s/\/home\/doe\//\/data\//": No such file or directory

find . type f -name Root | xargs perl -p -i -e "s/\/home\/doe\//\/data\//"
Worked as expected.
```


