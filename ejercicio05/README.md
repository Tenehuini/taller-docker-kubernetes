HEALTHCKECK: is a command used to determine the health of a running container. When a health check command is specified, it tells Docker how to test the container to see if it's working. It can be used in the Dockerfile as well as in a compose file. The syntax is HEALTHCHECK [OPTIONS] CMD command. Example: HEALTHCHECK CMD curl --fail http://localhost/ || exit 1

ONBUILD: adds to the image a trigger instruction to be executed at a later time, when the image is used as the base for another build. Useful if you are building an image which will be used as a base to build other images.

VOLUME: creates a mount point with the specified name and marks it as holding externally mounted volumes from native host or other containers. The value can be a JSON array, VOLUME ["/var/log/"], or a plain string with multiple arguments, such as VOLUME /var/log or VOLUME /var/log /var/db
