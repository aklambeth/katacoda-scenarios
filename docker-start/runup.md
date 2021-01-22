# Working with Containers #

## Creating a container ##
To create a running Container from our image use the ***docker run*** command `docker run <image_name>`  
however as containers by default run in their own isolated network namespace we have to tell Docker to open some ports to the outside world so we can interact with it. To do this we use the ***-p or --publish*** flag `-p <host port>:<inter>`. We can take a deeper look at container networking later.
It's also good practice to assign a name to our container with the ***-n --name*** flag. Docker will automatically generates and assigns a random name to the container if one is not provided.

> `--name rabbit1` *name the container 'rabbit1'*  
> `--publish 80:15672` *forward requests on the hosts port 80 to the containers internal port 15672 

Run the following command to Create and start a container using the rabbitmq image

`docker run --name rabbit1 --publish 80:15672 rabbitmq:3-management`{{execute}}

You'll see trace output written to the terminal as the container runs up. You should be able to see the following messages confirming that we have a running container instance.

```
[info] Management plugin: HTTP (non-TLS) listener started on port 15672 
[info] <0.777.0> Statistics database started. 
[info] <0.776.0> Starting worker pool 'management_worker_pool' with 3 processes in it 
[info] <0.9.0> Server startup complete; 3 plugins started. 
 * rabbitmq_management
 * rabbitmq_web_dispatch 
 * rabbitmq_management_agent  
```
 Remember we mapped the internal port 15672 to the hosts port 80. We should be able to view the management page by opening a new tab using the '**+**' button, and select **View Http Port 80**. You can login with the user name ***guest*** and password ***guest***

 When you're done go back to the Terminal window and press `ctrl+c`.  
 After a short pause the container will shut itself down and return you back to the command prompt after confirming it's stopped
 
 `Gracefully halting Erlang VM`

 Now try creating the container again.

 `docker run --name rabbit1 --publish 80:15672 rabbitmq:3-management`{{execute}}

That didn't work. It's telling us we've already created a container with that name earlier. We only stopped the container running, it still exists on our system. To delete the container we could use the docker ***rm*** command `docker rm rabbit1`. We'd could then create a new container with the same name, but we'd loose state. 

Next we'll take a look at some tools to manage our container.


