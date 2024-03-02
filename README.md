# Software-Quality-Lab-3

Harsh Tamakuwala - 100824220

## Objectives: 
1. Get Familiar with Docker and Kubernetes. 
2. Use Google Cloud Platform.
3. Deploy Maven WebApp over Google Kubernetes Engine (GKE).

## YAML Files
binarycalculator-deploy.yaml:
  ```yaml
  apiVersion: apps/v1
  kind: Deployment
  metadata:
    name: binarycalculator-deployment
  spec:
    replicas: 1
    selector:
      matchLabels:
        app: binarycalc
    template:
      metadata:
        labels:
          app: binarycalc
      spec:
        containers:
          - image: northamerica-northeast2-docker.pkg.dev/feisty-tempest-415720/sofe3980u/binarycalculator
            name: binarycalculator
            ports:
              - containerPort: 8080
                name: binarycalc
  ```
binarycalculator-service.yaml:
  ```yaml
  apiVersion: v1
  kind: Service
  metadata:
    name: binarycalculator-service
  spec:
    type: LoadBalancer
    ports:
      - port: 8080
    selector:
      app: binarycalc
  ```
