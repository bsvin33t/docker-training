What is a good dockerfile?

- A good dockerfile creates an image with minimum size footprint.
- Keeps the build time low.
- Ensures that the container is not exposed to unrelated vulnerabilities.
- Easy to read and maintain.

By doing the above we get the below results

- Making it easy for the collabrators to work with your project by keeping the image size low.
- Improves development agility as small Docker images means faster build time and faster deployment.
- Reducing the attack surface by excluding packages that are not used.
- Reduced network latency and faster transfer of Docker images over the web.
