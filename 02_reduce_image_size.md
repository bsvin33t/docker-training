# How to write a good dockerfile

In my previous [blogposts](link here), I spoke about why to optimize dockerfile. This brings us to the next question, how to do it.
In this blogpost(of many), I am going to discuss, how we can optimize dockerfiles.

### Techniques to reduce image size

The first topic that I'm going to tackle is, trying to keep the a image size low.

#### Selecting the base image variant.

Usually, when we start to work with docker, we need a base image.
With docker, we have an option to start with OS, then apply a programming language.
Another alternative is to use the programming language's official image.

There are multiple variants of base image, a few examples that are popular in ruby community are below:

| Variant         | Size  |                                                                         |
|-----------------|-------|-------------------------------------------------------------------------|
| ruby:2.7        | 842mb | Full Debian operating system with ruby installed.                       |
| ruby:2.7-slim   | 149mb | Only contains the minimal packages needed to run ruby.                  |
| ruby:2.7-alpine | 52mb  | Alpine Linux is much smaller than most distribution base images (~5MB). |

If you are unsure about the future requirements of the project, I would recommend using the debian based(centos/ubuntu) image.

I would like to give you all a handy table that you can use to decide between Alpine and Debian images.

| Ubuntu/Debian                 | Alpine                       |
|-------------------------------|------------------------------|
| Built around GNU C libarary   | Built around musl C libarary |
| more mature/stable            | less mature/stable           |
| More 3rd party packages       | Fewer 3rd party packages     |
| Less memory effecient         | More memory effecient        |
| Bigger base image footprint   | Smaller base image footprint |
| Suitable for complex projects | Suitable for simple projects |


#### Personal experience

I started with alpine, as it impressed me with the small size. Later I discovered that I wanted to use GEOS(link here). 
But the alpine  didn't have an implementation for this.

This made me change from using alpine and rewriting all my dockerfiles to use ubuntu as the base image. 
The rewrite was a painful and time consuming process.

Even though I didn't have a great experience with alpine, I would go with it if the scope of the project is limited.
