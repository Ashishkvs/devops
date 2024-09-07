# Docker provides a single command that will clean up any resources — images, containers, volumes, and networks — that are dangling (not associated with a container):
docker system prune
# additionally remove any stopped containers and all unused images (not just dangling images), add the -a flag to the command
docker system prune -a
# To delete all containers including its volumes use
docker rm -vf $(docker ps -aq)
# To delete all the images,
docker rmi -f $(docker images -aq)
# Use this to delete everything
docker system prune -a --volumes



# docker user group add
sudo usermod -aG docker $USER

# docker stop all container
docker stop $(docker ps -a -q)

# docker start all container
docker start $(docker ps -a -q)
