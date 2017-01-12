The following steps will build a mysql docker image for PowerPC LE
on the Intel host

Download the sample code

`
git clone https://github.com/bpradipt/docker-mysql.git
cd docker-mysql
`{{execute}}


Check the Dockerfile content. The key is the multiarch base image used in
the FROM directive

`
cat Dockerfile.multiarch.ppc64le
`{{execute}}


Build the docker image for Power

`
docker build -t ppc64le/mysql -f Dockerfile.multiarch.ppc64le .
`{{execute}}


Spawn a container 
`
docker run -itd --name mysql -e MYSQL_ROOT_PASSWORD=password -e MYSQL_USER=user -e MYSQL_PASSWORD=pass -e MYSQL_DB=test -P ppc64le/mysql
`{{execute}}


`docker ps
`{{execute}}


Check the CPU architecture of the running MySQL container
`
docker exec -it mysql uname -m
`{{execute}}
