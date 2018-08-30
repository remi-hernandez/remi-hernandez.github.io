= Docker bro
// See https://hubpress.gitbooks.io/hubpress-knowledgebase/content/ for information about the parameters.
// :hp-image: /covers/cover.png
// :published_at: 2019-01-31
// :hp-tags: HubPress, Blog, Open_Source,
// :hp-alt-title: My English Title


cmd    - action
docker ps     - list all containers
docker exec   - run a command in a running container


docker-compose down --remove-orphans
docker-compose up -d (detach)

https://stackoverflow.com/questions/33715499/what-is-the-difference-between-docker-compose-up-and-docker-compose-start


== Debug plex

Check the logs of what's inside of the container. e.g.: we want to check the logs of plex. For it we want to have a shell running inside our container. We will find the name of our container using `docker ps`, let's say "plex_container" and the use `docker exec -it plex_container`.

When the container is setted up don't forget to create a ssh tunnel for the port forwarding `ssh -N -L 3200:server.com:32400 server.com ` and then go on `http://localhost:3200/web/index.html` to claim the server.


