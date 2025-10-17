## Portainer

docker hubのようなUIをウェブ上で提供する

```sh
sudo docker run -d \
   --name portainer \
   --restart always \
   -p 9000:9000 \
   -v /var/run/docker.sock:/var/run/docker.sock \
   -v /volume1/docker/configs/portainer:/data \
   portainer/portainer-ce:latest
```


