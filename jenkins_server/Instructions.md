# Instructions to create jenkins server in docker container

1. Install jenkins docker image with `sudo docker pull jenkins`
2. Now jenkins is downloaded you can run the image
    `sudo docker run --detach --publish=49001:8080 --volume=/home/alex/jenkins_server:/var/jenkins_home --tty --name="my_jenkins_1" jenkins`
    note: the volume user name is where the jenkins data is stored.
3. `sudo docker logs my_jenkins_1` will output the log and reveal the admin password.
4. Use the password to access jenkins by opening a browser to `http://localhost:49001` and following the instructions,
5. Installing using docker-compose -
    Use the files included in this repo, the `plugins.txt` file will install `nodejs` and it dependencies. Installing plugins through Docker we have to provide all dependencies for this plugin also. 
    So the above list provides all plugins in the dependency tree of `nodejs`. The list is in the format of `pluginID:version` 
    and this information for each plugin was gleaned from the [Jenkins plugins directory online](https://plugins.jenkins.io).
6. With the terminal or cli open in this folder send `sudo docker-compose build`. This will create a new image called *jenkins_my-jenkins-setup* 
    which contains all the Jenkins plugins listed in `plugins.txt`. The build process lists out all the plugins that were installed.

    Now start the new Jenkins container with `sudo docker-compose up` and open `http://localhost:49001` in the browser.
    You will not be taken to the setup screen again since we reused the same volumes created above.
    You will be asked for the username and password. Enter the same admin username and password that you created during the setup process.
    Once you are logged in, you can start using Jenkins like before but with the new plugins installed.   
    
More details on how to use the Jenkins Docker image can be found from the [Dockerhub page for Jenkins](https://hub.docker.com/_/jenkins/).

Full instructions from [Jenkins Docker Image Example](https://examples.javacodegeeks.com/devops/docker/jenkins-docker-image-example/)
