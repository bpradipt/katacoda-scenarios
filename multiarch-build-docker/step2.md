Since 'docker build' cannot mount host volumes, we'll be using multiarch images from Dockerhub 
which packages qemu-ppc64le-static along with the base image.
More details on multiarch docker images is available here - https://eyskens.me/multiarch-docker-images/

The below command will run the multiarch image for ppc64le and display /usr/bin/qemu-ppc64le-static

`
docker run  multiarch/ubuntu-core:ppc64el-xenial ls /usr/bin/qemu-ppc64le-static
`{{execute}}


We'll be using this base image to create a PowerPC LE docker image in the next step

