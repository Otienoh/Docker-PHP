Docker Image for [Siege](http://www.joedog.org/siege-home/)
====

How to use.
----

### setup

```console
$ git clone https://github.com/yokogawa-k/docker-siege.git
$ cd docker-siege
$ docker build -t otienojulie/siege .
```

### Performance test

```console
$ docker run --rm -t otienojulie/siege -d1 -r10 -c25 example.com
```
