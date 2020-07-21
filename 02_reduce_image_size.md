# How to write a good dockerfile

In my previous blogposts, I spoke about why to optimize dockerfile. This brings us to the next question, how to do it.
In this blogpost of many, I am going to discuss, how we can optimize dockerfiles, so that we can achieve software nirvana.

### Techniques Reduce image size

The first topic that I'm going to tackle is, trying to keep the a image size low.

You know from my previous blogposts(link here) why having a small docker image is great for the project.
Now we look at how to do it.

#### Selecting the base image variant.

Usually, when we start to write code, we need an OS.
With docker, we start with a base image, we start with OS, then apply a programming language.
But this can be changed by using the official programming language's image.

There are multiple variants of base image, a few examples that are popular in ruby community are below:

| Variant         | Size  |                                                                         |
|-----------------|-------|-------------------------------------------------------------------------|
| ruby:2.7        | 842mb | Full Debian operating system with rub installed.                        |
| ruby:2.7-slim   | 149mb | Only contains the minimal packages needed to run ruby.                  |
| ruby:2.7-alpine | 52mb  | Alpine Linux is much smaller than most distribution base images (~5MB). |


I don't recommend using alpine, even though there are a lot of blogs that you use it.
I say this because compared to debian, even though this is lightweight, I would still go with debian, 
as the operating system is run on hundreds of thousand of projects, you have a huge commnuty to fall back on for support, 
the number of community provided packages and a battle tested operating system.

Alpine inherently does not provide any kind of additional security benefits for the container, even though it is of smaller size.

I started alpine, as I was impressed with the small size, later I discovered that I wanted to use Geos for my porject, but
the alpine image didn't really have an implementation for this. 

This made me change from using alpine and rewriting all my dockerfiles to use ubuntu as the base image.
For each of the operating system, the commands that are run are different, which is what triggered the rewrite.

Also, from a hear-say, I got to know that alpine with python/nodejs and postgres brings in some serious performance challenges, 
which might be because of postgres package of the OS under heavy load. 

Even though I didn't have a great expereience with alpine, I would go with it if I want to do somethig simple, 
like downloading data from an API endpoint, and generating a CSV to upload to S3 or exposing it web,
or providing an interface to your team to upload/download data.
Generally, if the scope of the project is going to be very limited and it is not going to change much, alpine could be an option.

Even after all this, I would always say YMMV and suggest that you use whatever your project calls for.

In conclusinon, I would like to give you all a handy table that you can use to decide between alpine and debeian images.


| Ubuntu/Debian                 | Alpine                       |
|-------------------------------|------------------------------|
| Built around GNU C libarary   | Built around musl C libarary |
| more mature/stable            | less mature/stable           |
| More 3rd party packages       | Fewer 3rd party packages     |
| Less memory effecient         | More memory effecient        |
| Bigger base image footprint   | Smaller base image footprint |
| Suitable for complex projects | Suitable for simple projects |

