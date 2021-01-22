# Docker Containers and Images

In Docker world Images are the definition from which the Containers are created.  
In programming world an Image is as a Class or Object and the Container is an instance of that Class. This is why running Containers are referred to as instances. 

You're able to create many instances of an application from a single Image. We can do this because Containers are not only isolated processes they are stateless. When a container is destroyed / deleted any changes made whilst it was running like configuration is lost and any new containers created will revert back to the original state.
As each container is an isolated reproducible clone of the Image we can be sure it will work across different systems. 

## Working with Images ##

Images are portable, are usually distributed via remote repository's such as Docker Hub. Before we can do anything we need to find an Image and 'Pull' it down from the repository.

To Search for an image, in this case 'rabbitmq' run the command 

`docker search rabbitmq`{{execute}}

There's a lot of Images, these may be derived from a common ***base image*** or simply branched from the official rabbitmq Image. We want to ***pull*** down the official image.

`docker pull rabbitmq`{{execute}}

Once that's done we can use ***docker image*** command to list out the images we have on our system.

`docker image ls`{{execute}}

Note that it's pulled the latest version by default.  
If we want to pull a specific version we use image ***tags***. Checking out the dockers registry page we can see all the tags that are available.  
We want the image tagged **3-management** which contains a web interface we can connect to in the next chapter. To get this append the tag name onto the end of the image name **rabbitmq:3-management**.

`docker pull rabbitmq:3-management`{{execute}}

Get the list of images with `docker image ls`{{execute}}  
To remove the old image use the **rm** command `docker image rm rabbitmq`{{execute}}  

Next we need to run ***up*** a container from our Image.

