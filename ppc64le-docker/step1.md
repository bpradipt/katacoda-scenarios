Download and Install the Qemu binary. 
QEMU is an open source machine emulator and virtualizer.

When used as a machine emulator, QEMU can run OSes and programs made for one machine - eg PowerPC LE
on a different machine - e.g on Intel laptop.
`
wget https://github.com/multiarch/qemu-user-static/releases/download/v2.7.0/qemu-ppc64le-static.tar.gz
tar zxvf qemu-ppc64le-static.tar.gz
`{{execute}}


Register Qemu as PowerPC LE binary handler. This is the key thing. 
We'll be using multiarch/qemu-user-static docker image for this.

`
docker run --rm --privileged multiarch/qemu-user-static:register
`{{execute}}


