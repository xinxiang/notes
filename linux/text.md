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
