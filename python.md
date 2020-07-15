# List installed modules
```
$ pip freeze
...
Django==2.1.7
feedparser==5.2.1
Flask==1.0.2
flask-marshmallow==0.9.0
Flask-SQLAlchemy==2.3.2
...
```

```
$ python
Python 3.6.9 (default, Nov  7 2019, 10:44:02) 
[GCC 8.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> help("modules")
...
_pydecimal          django              pickletools         traceback
_pyio               doctest             pip                 tracemalloc
_random             dummy_threading     pipes               tty
_sha1               easy_install        pkg_resources       turtle
...
```

Install pip on Ubuntu
```
sudo apt install python3-venv python3-pip
```
Ref: https://packaging.python.org/guides/installing-using-linux-tools/
