# What is a good dockerfile?

Dockerfile Best practices part 2 (find Part 1 [here](https://www.linkedin.com/pulse/dockerfile-best-practices-buildkit-bhushan-lodha))

- A good dockerfile creates an image of a smaller size.
- Keeps the build time low.
- Ensures that the containers are not exposed to unrelated vulnerabilities.
- Easy to read and maintain.


By doing the above we get the below results

- Making it easy for the collaborators to work with your project by keeping the image size low.
- Improves development agility as small Docker images mean faster build time and faster deployment.
- Reducing the attack surface by excluding packages that are not used.
- Reduced network latency and faster transfer of Docker images over the web.

Here is link to the webinar I did recently that covers the topic: https://youtu.be/5kjXh6DCqGk

Here is the link to the slides: https://www.slideshare.net/bhushanlodha/dockerfile-best-practices-236920219

If you liked what you saw, and you want to hire me or want my advice, contact me at bhushanlodha[at]gmail.com
