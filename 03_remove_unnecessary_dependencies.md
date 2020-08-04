## Remove unnecessary dependencies

There are 2 things that we see. 

- Use the flag, no install recommends.
With this, only the main dependencies are installed, and not the recommended or the suggested packages.

- Avoid installing packages that are not needed to run your app. Eg: curl, vi, ssh and others.

In some projects, I was able to reduce the size by close to 40% of the size. 
Take for instance GEOS, with the recommends, it is of size:
Now, the same, without recommends, it is of size: 

``` dockerfile
RUN apt-get install --no-install-recommends\
    build-essential \
    lib-pq-dev \
    ssh # Unnecessary
```
