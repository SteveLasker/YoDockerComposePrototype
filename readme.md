# YoDockerComposePrototype
Prototype for adding compose functionality to yo docker

[yo docker](http://aka.ms/yodocker) creates Dockerfiles and bash scripts to build and run your docker containers.
This prototype is the next step to using docker-compose.yml files to configure multiple containers for multiple environments, such as dev, staging and production.
Dev likely has unique configurations for things like mapping the source directory to the host machine so you can edit your code with your editor, save it and reload your app with tools like nodemon. 
Staging would need to remove this functionality.

## Use of docker-machine
Rather than put the functionality of switching hosts within the bash script, we will defer the target configuration using docker-machine.

# Using this Prototype
[yo docker](http://aka.ms/yodocker) uses `dockerTask.sh` to build and run containers. by passing options and parameters to you can switch between different configurations

## Dev Environment ##
Will create and run a container that enables local editing of content files on your host machine enabling you to refresh your pages running in the container seeing the changes. 
This uses the volume mapping feature, along with nodemon to enable local development 

`dockerTask compose dev` 
Uses the following files:
- docker-compose.yml
- docker-compose.dev.yml
- Dockerfile.dev

Will execute the following command `docker-compose -f docker-compose.yml -f docker-compose.dev.yml up -d --force-recreate` 


## Staging Environment ##
Will create and run a container that represents your staging environment. This emulates the production ready image without any local mounted volumes or debugging. 

`dockerTask compose staging` 
Uses the following files:
- docker-compose.yml
- docker-compose.staging.yml
- Dockerfile

Will execute the following command `docker-compose -f docker-compose.yml -f docker-compose.staging.yml up -d --force-recreate` 


