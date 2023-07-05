
# cmlabs-devops-freelance-test

This is configuration file to deploy nginx service in 2 nodes with 3 replicas each node. If kubernetes cluster for deployment have used 2 nodes, it could used deployment-2-node.yaml.

```sh
kubectl apply -f deployment-2-node.yaml
```

If you use a Kubernetes cluster with multiple nodes, you need to specify the node that will deploy this nginx service by adding a label to the node, for example node=nginx.

```sh
kubectl label nodes <your-node-name> node=nginx
```
Modify file deployment-multi-node.yaml with your label on key and values.

```sh
affinity:
nodeAffinity:
    requiredDuringSchedulingIgnoredDuringExecution:
    nodeSelectorTerms:
    - matchExpressions:
        - key: node
        operator: In
        values:
        - nginx

```

Then deploy your configuration

```sh
kubectl apply -f deployment-multi-node.yaml
```


