### portainer 설치
```sh
docker run -d -p 8000:8000 -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce
```

```docker
version: "2"
services:
  bookstack:
    image: ghcr.io/linuxserver/bookstack
    container_name: bookstack
    environment:
      - PUID=1026
      - PGID=100 
      - APP_URL=http://YourNASIP:6875
      - DB_HOST=bookstack_db
      - DB_USER=bookstack
      - DB_PASS=yourdbpass
      - DB_DATABASE=bookstackapp
    volumes:
      - /volume1/docker/bookstack:/config
    ports:
      - 6875:80
    restart: always
    depends_on:
      - bookstack_db
  bookstack_db:
    image: ghcr.io/linuxserver/mariadb
    container_name: bookstack_db
    environment:
      - PUID=1026
      - PGID=100
      - TZ=Europe/Bucharest
      - MYSQL_ROOT_PASSWORD=yourdbpass
      - MYSQL_DATABASE=bookstackapp
      - MYSQL_USER=bookstack
      - MYSQL_PASSWORD=yourdbpass
    volumes:
      - /volume1/docker/bookstack:/config
    restart: always
```
