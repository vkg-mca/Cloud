docker run --name docker-compose-ui -p 50055:5000 -w /opt/docker-compose-projects/ -v /var/run/docker.sock:/var/run/docker.sock francescou/docker-compose-ui:1.13.0

http://localhost:50055/#/