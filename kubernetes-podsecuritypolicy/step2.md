Kubernetes a combination of components, each run on the Master node. The Master is a single node which manages the cluster and the containers running it in. The master will launch new containers, configure networking and provide health information.

The library _hyperkube_ allows you to launch the different components. The first component is the API server. The API processes requests from the master and store information in the etcd cluster.
`
docker run -d --name=api \
    --net=host --pid=host --privileged=true \
    gcr.io/google_containers/hyperkube:v1.3.6 \
    /hyperkube apiserver \
    --insecure-bind-address=0.0.0.0 \
    --service-cluster-ip-range=10.0.0.1/24 \
    --etcd_servers=http://127.0.0.1:4001 \
    --runtime-config=extensions/v1beta1/podsecuritypolicy=true \
    --admission-control=NamespaceLifecycle,LimitRanger,ServiceAccount,ResourceQuota,PodSecurityPolicy \
    --v=2
`{{execute}}

##### Options

_insecure-bind-address_ binds the API to all IP addresses and makes it available via HTTP. This is useful for development purposes as it removes the need for certifications but should not be used in production.

_service-cluster-ip-range_ provides an IP range all containers will use.

_etcd_servers_ indicates where the API can find the etcd servers. This is a comma separated list of HTTP endpoints

_runtime-config_ provides a way to pass additional options to API server

_admission-controller_ specify the admission controllers to be used

_cluster_name_ provides a friendly name to the cluster.
