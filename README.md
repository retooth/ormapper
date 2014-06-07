ormapper
========

An object-relational mapper I originally did for shmudder 3 years ago but now decided to list independently.
I wrote it out of spite, because i was frustrated with apt-get having a version conflict between python and sqlalchemy.

There is a "kind of" documentation on the shmudder wiki([here](https://github.com/retooth/shmudder/wiki/Initializing,-Loading,-Patching) and [here](https://github.com/retooth/shmudder/wiki/Understanding-the-database).). 

It has some cool features, the main feature being an attribute distributor, that makes it possible to use multiple inheritance and instanciation on every level. this means, that things like:

``` python
class Foo (Persistent):
    foo = Integer()

class Bar (Persistent):
    bar = String()
    
class FooBar (Foo, Bar):
    stuff = Boolean()
    
f = Foo()
f.foo = 2
fb = FooBar()
fb.foo = 3
fb.bar = "barfoo"
```  

with f and fb being Persistent on their own, are possible. not even sqlalchemy can do this. However: It has a weird init/loading mechanism, that was inspired by pickle and pickle-based libs. So it's more a better pickle than a substitute for sqlalchemy. It also only uses sqlite as backend without being configurable. 
