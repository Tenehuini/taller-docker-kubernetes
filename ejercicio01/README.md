docker run --name nginx-test -v "$(pwd)":/usr/share/nginx/html:ro -p 80:80 -d nginx

curl localhost:80/nombre.html
