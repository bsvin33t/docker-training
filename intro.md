What is a good dockerfile?


- A good docker file has a minimum size footprint.
    1. Making it easy for the collabrators to work with your project by keeping the file size low.
    2. Memory footprint of the docker process is low.
    3. Reducing the attack surface by excluding packages that are not used.
    1. network latency – need to transfer Docker image over the web
    1. storage – need to store all these bits somewhere
    1. service availability and elasticity – when using a Docker scheduler, like Kubernetes, Swarm, Nomad, DC/OS or other (the scheduler can move containers between hosts)
    1. security – do you really, I mean really need the libpng package with all its CVE vulnerabilities for your Java application?
    1. development agility – small Docker images == faster build time and faster deployment
