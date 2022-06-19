¿Cuántos contenedores se están ejecutando? (pueden verlo en el archivo docker-compose-jobvacancy.yml y también ejecutando docker ps)
2 containers (web and db)

<br />
¿Cuales son las imágenes en las que están basados los mencionados contenedores?
The images are nicopaez/jobvacancy-ruby:1.3.0 for web and postgres for db

<br />
¿Puedes leer el docker-compose-jobvacancy.yml y describir lo que hace cada una de sus lineas?
<pre>
version: '2' is the version of the yml file<br />
services: list the services <br />
  web: name of the image <br />
    image: nicopaez/jobvacancy-ruby:1.3.0  the image used <br />
    links: <br /> Link to containers in another service
      - db <br />
    ports: ports exposed <br />
      - "3000:3000" <br />
    environment: sets environment variables <br />
      PORT: "3000" <br />
      RACK_ENV: "production" <br />
      DATABASE_URL: "postgres://postgres:Passw0rd!@db:5432/postgres" <br />
    depends_on: Express dependency between services <br />
      - db <br />
  db: name of the image <br />
    image: postgres the image used <br />
    environment: sets environment variable <br />
      POSTGRES_PASSWORD: Passw0rd! environment variable <br />
</pre>
<br />
Dado que cada contenedor corre en forma aislada ¿Cómo es posible que esos contenedores se vean entre sí?
Because they are in the same network. Using docker network ls we see: <br />
NETWORK ID     NAME                  DRIVER    SCOPE <br />
c80167d357a6   ejercicio07_default   bridge    local <br />
Then we can use docker network inspect c80167d357a6 and the result is: <br />
<pre>
[
    {
        "Name": "ejercicio07_default",
        "Id": "c80167d357a6d9fe0fadc82810a61f1b1172e4cdcfefab96ecaa7e5bf20c743e",
        "Created": "2022-06-19T13:17:45.2508466-03:00",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": null,
            "Config": [
                {
                    "Subnet": "172.19.0.0/16",
                    "Gateway": "172.19.0.1"
                }
            ]
        },
        "Internal": false,
        "Attachable": false,
        "Ingress": false,
        "ConfigFrom": {
            "Network": ""
        },
        "ConfigOnly": false,
        "Containers": {
            "75433bff9692984920c1165ee345b469a0f9692d0a4584fee165ba9a2f14da0d": {
                "Name": "ejercicio07_db_1",
                "EndpointID": "8b87b1c4dfeec641a95247266c4818a94475dddffba28ce8ca97247e44fe894b",
                "MacAddress": "02:42:ac:13:00:02",
                "IPv4Address": "172.19.0.2/16",
                "IPv6Address": ""
            },
            "f4b34c1947ea447c7b8596198d6f754f9fed639d89c65a04e9c0745b96713f7d": {
                "Name": "ejercicio07_web_1",
                "EndpointID": "1487213b9ab2fc4d398b14e27a558e220f4a6f3aa3a2d338f4aace3b20cd6542",
                "MacAddress": "02:42:ac:13:00:03",
                "IPv4Address": "172.19.0.3/16",
                "IPv6Address": ""
            }
        },
        "Options": {},
        "Labels": {}
    }
]
</pre>
<br />
The two containers listed have the id shown in docker container ls: <br />
<pre>
CONTAINER ID   IMAGE                            COMMAND                  CREATED         STATUS         PORTS                                       NAMES
f4b34c1947ea   nicopaez/jobvacancy-ruby:1.3.0   "/jobvacancy/start_a…"   5 minutes ago   Up 5 minutes   0.0.0.0:3000->3000/tcp, :::3000->3000/tcp   ejercicio07_web_1
75433bff9692   postgres                         "docker-entrypoint.s…"   5 minutes ago   Up 5 minutes   5432/tcp                                    ejercicio07_db_1
</pre>

