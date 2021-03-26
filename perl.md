# Where Is Perl Module Installed
```
perl -MPlack::Middleware::Auth::Doe -e 'print $INC{"Plack/Middleware/Auth/Doe.pm"}'

perldoc -l Plack::Middleware::Auth::Doe
```

**Ref**: https://stackoverflow.com/questions/1557959/how-can-i-find-out-where-a-perl-module-is-installed

# Hash
```
my %hash = ();
$hash{key} = value;

my %hash = (key => val);
```

# Hash Reference
```
my $hash_ref = {};
$hash_ref->{key} = value;

my $hash_ref = { $key => $val};
```

## Reference
* https://www.cs.mcgill.ca/~abatko/computers/programming/perl/howto/hash/


# Comparison
* string: eq, ne, cmp, lt, gt, le, ge
* number: ==, !=, <=>, <, >, <=, >=
## Reference
* https://users.cs.cf.ac.uk/Dave.Marshall/PERL/node37.html
