# AngularDocker

## Steps to containerize an angular application.

## Create new project/application

```ng new AngularDocker```

![Alt desc](https://github.com/nj11/AngularDocker/blob/master/screenshots/screenshot1.png)


## Make sure project runs successfully

```ng serve```

#### Steps for containerization of angular application.  

![Alt desc](https://github.com/nj11/AngularDocker/blob/master/screenshots/screenshot2.png)

##### Reference for docker multi stage builds - https://docs.docker.com/develop/develop-images/multistage-build/      
        
        1.Run docker desktop

        2.Create Dockerfile for project under root directory.

        3.Login to docker using ```docker login ``` command

        4.Docker delete images (if needed) from powershell

         ```$images = docker images -a -q
            foreach ($image in $images) { docker image rm $image -f }```

         ```docker build -t <dockerusername>/angulardocker .```
        
        5 Run ```docker images``` to make sure image was created.
         
          REPOSITORY                    TAG                 IMAGE ID            CREATED              SIZE
          natashajuneja/angulardocker   latest              208415c0d413        9 seconds ago        34.5MB
          node                          12.16.1-alpine      f77abbe89ac1        11 months ago        88.1MB
          nginx                         1.15.8-alpine       b411e34b4606        2 years ago          16.1MB
          
               
        6.  
            ```docker run  -p 4200:80   <dockerusenname>/angulardocker``` --will run on localhost:4200
            
                           
        7.Check running containers.
        ```docker ps```
        
        7.Stop all running containers.
        ```docker rm -f $(docker ps -a -q)```
                        
       5.Run docker push command with the tag name being like username/repository name
       
       ```docker push <dockerusername>/angulardocker```

