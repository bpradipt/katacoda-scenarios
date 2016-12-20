iCreate a cluster wide policy to ensure
1. Prevent users from creating privilege containers
2. Prevent process(es) inside the container to run as the ‘root’.

The policy config YAML is shown below:
```json
{
  "kind": "PodSecurityPolicy",
  "apiVersion":"extensions/v1beta1",
  "metadata": {
    "name": "noroot"
  },
  "spec": {
      "privileged": false,
      "seLinux": {
          "rule": "RunAsAny"
      },
      "supplementalGroups": {
          "rule": "RunAsAny"
      },
      "runAsUser": {
          "rule": "MustRunAsNonRoot"
      },
      "fsGroup": {
          "rule": "RunAsAny"
      },
      "volumes": ["*"]
  }
}
```

Let's apply the policy

`kubectl create -f https://raw.githubusercontent.com/bpradipt/examples/master/kubepodsecpolicy/noroot.yaml`{{execute}}
