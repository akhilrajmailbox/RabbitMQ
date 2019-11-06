# RabbitMQ cluster on Azure kubernetes with StatefulSets

RabbitMQ is a general purpose messaging solution, often used to allow web servers to respond to requests quickly instead of being forced to perform resource-heavy procedures while the user waits for the result.

### Create Namespace for datamall dependencies
```
kubectl create ns rabbitmq-cluster
```

### Configmap for RabbitMQ Cluster
```
kubectl create secret generic rabbitmq-config --from-literal=erlang-cookie=c-is-for-cookie-thats-good-enough-for-me -n rabbitmq-cluster
```

### Create custom storageclass with parameter : "allowVolumeExpansion"
```
kubectl apply -f pvc-storageclass.yaml
```

### Deploy RabbitMQ cluster
```
kubectl apply -f rabbitmq-deployment.yaml -n rabbitmq-cluster
```

### Create RabbitMQ Service
```
kubectl apply -f rabbitmq-service.yaml -n rabbitmq-cluster
```

[reference](https://wesmorgan.svbtle.com/rabbitmq-cluster-on-kubernetes-with-statefulsets)


