[GNU Parallel](https://www.gnu.org/software/parallel/)

# Check number of cores
```
grep -c ^processor /proc/cpuinfo
nproc --all
```

# Process files in parallel
* Save the commands into a runlist: cmd 
```
...
text2solrdoc T30150
text2solrdoc T30160
text2solrdoc T30170
text2solrdoc T30180
...
```
* Run the runlist with parallel
```
parallel < runlist
```
**Note:** Do not let the commands output to the same file.
