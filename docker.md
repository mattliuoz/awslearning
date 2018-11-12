### dockerfile reference
https://docs.docker.com/engine/reference/builder/#copy

### clean up
docker rm $(docker ps -a -q) && docker rmi $(docker images -q --filter "dangling=true")
