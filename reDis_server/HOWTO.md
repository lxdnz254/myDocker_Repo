# Create a redis webserver

Using `docker-compose up` inside this directory docker-compose will read the `Dockerfile` and create a redis webserver container.
It creates an image from ubuntu 14.04 and installs java_1.8 then reading the maven file `pom.xml` it will assemble the webserver script.
Once running use these commands:
* `docker-machine ip default` - this will output the ip address of the docker-machine
* `curl -X PUT --data "new task" http://192.168.99.100:8000/todos` sends "new task" to the machine (if that is the ip address), the port is set to 8000.
* `curl -X GET http://192.168.99.100:8000/todos` will output any PUT's on the webserver.

Notes: `docker-machine` must be active before running `docker-compose up`
