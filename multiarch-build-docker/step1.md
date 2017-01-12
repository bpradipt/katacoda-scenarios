Register Qemu as PowerPC LE binary handler. This leverages binfmt_misc capability of 
the Linux kernel and is the key thing. More details on binfmt_misc is available here 
- https://en.wikipedia.org/wiki/Binfmt_misc

Check the host CPU architecture.

`
uname -m
`{{execute}}


The command below will register interpreters to run binaries belonging to specific architecture.

`
docker run --rm --privileged multiarch/qemu-user-static:register
`{{execute}}


Verify.

`
cat /proc/sys/fs/binfmt_misc/ppc64le
`{{execute}}


Any ppc64le binary (magic - 7f454c460....) will be executed with /usr/bin/qemu-ppc64le-static.

