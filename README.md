# KUBERNETES

*NOTE* : WE CAN INSTALL KUBERNETES IN MANY WAYS 

## STEP 1: CONFIGURE AWS CLI
## STEP 2: INSTALL EKSCTL FOR K8S CLUSTER CREATION

```bash
# for ARM systems, set ARCH to: `arm64`, `armv6` or `armv7`
ARCH=amd64
PLATFORM=$(uname -s)_$ARCH

curl -sLO "https://github.com/eksctl-io/eksctl/releases/latest/download/eksctl_$PLATFORM.tar.gz"

# (Optional) Verify checksum
curl -sL "https://github.com/eksctl-io/eksctl/releases/latest/download/eksctl_checksums.txt" | grep $PLATFORM | sha256sum --check

tar -xzf eksctl_$PLATFORM.tar.gz -C /tmp && rm eksctl_$PLATFORM.tar.gz

sudo install -m 0755 /tmp/eksctl /usr/local/bin && rm /tmp/eksctl
```
## STEP 3: INSTALL KUBECTL FOR K8S CLUSTER INTERACTION

```bash
curl -O https://s3.us-west-2.amazonaws.com/amazon-eks/1.33.3/2025-08-03/bin/linux/amd64/kubectl
```
```bash
chmod +x ./kubectl
```
```bash
sudo mv kubectl /usr/local/bin/kubectl
```

## STEP 4: CHECK WHETHER INSTALLED PROPERLY
```bash
eksctl version
kubectl version
```
## STEP 5: NOW WE WILL CREATE A MANAGED NODE GROUP or IN SHORT A CLUSTER WITH A MASTER AND WORKER NODES

*NOTE: A MANAGED NODE GROUP IS THE SET OF AWS WORKER NODES(INSTANCES) THAT AWS WILL CREATE AND MANAGE ON ITS OWN*
```bash
eksctl create cluster --config-file=eks.yaml
```
```bash
eksctl delet cluster --config-file=eks.yaml
```

## SHOW WORKER NODES IN A WORKSTATION

```bash
kubectl get nodes
```

## RESOURCES DISCUSSED IN THIS REPO

### NAMESPACE

Creation of namespace 
```bash
kubectl apply -f namespace.yaml
```

Cheking of namespace created 
```bash
kubectl get namespace
```

Deletion of namespace 
```bash
kubectl delete -f namespace.yaml
```

### PODS

Creation of PODS
```bash
kubectl apply -f pod.yaml
```

Cheking of namespace created 
```bash
kubectl get pods
```

Deletion of namespace 
```bash
kubectl delete -f pod.yaml
```