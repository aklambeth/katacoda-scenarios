### Docker Start ###

Use the docker ***start*** command to run the container back up again `docker start rabbit1`{{execute}}.

Notice this time it didn't start in the terminal windows, it left us at the command prompt. The container is now running as a background task. Use the docker ***ps*** command to view a list of all our running containers `docker ps`{{execute}}  
As well as it's name we can the containers id, parent image and ports. Notice we have host port 80 mapped to the containers internal `0.0.0.0:80->15672/tcp`

We can issue an API command on port 80 to rabbitmq.

`curl -i -u guest:guest -H "content-type:application/json" -XPUT http://localhost/api/vhosts/dev1`{{execute}}

https://[[HOST_SUBDOMAIN]]-80-[[KATACODA_HOST]].environments.katacoda.com

## Monitoring Logs ##

If we just need to view the containers output run the command `docker logs rabbit1`{{execute}}. To keep **following** the output without returning to the command prompt use the 'logs' ***-f*** suffix `docker logs -f rabbit1`{{execute}}. `Ctrl+c` will return to the command prompt without stopping the container.

## Stopping a running container ##

To stop an already running container use:

`docker stop rabbit1`{{execute}}

## Docker Attach ##

If we need to connect back to the running container we could use the command `docker attach rabbitmq`. We would then monitor the event log or stop the container with `ctrl+c` but i prefere to use the above commands.
