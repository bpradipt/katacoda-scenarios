Let's create a Pod with privileged:true and see what happens ?
The Pod yaml is shown below:

```json
apiVersion: "v1"
kind: "Pod"
metadata:
 name: "mysql"
 labels:
   name: "db"

spec:
    containers:
      - name: "mysql"
        image: "mysql"
        imagePullPolicy: "IfNotPresent"
        securityContext:
           privileged: true
           capabilities:
              add: ["SETFCAP"]
        env:
           - name: MYSQL_ROOT_PASSWORD
             value: password
        ports:
          - containerPort: 3306
```

`kubectl create -f https://raw.githubusercontent.com/bpradipt/examples/master/kubeyamls/podex2.yaml`{{execute}}
