# KIND - Kubernetes clusters inside Docker


## 1. Installing KIND and kubectl
Install KIND and kubectl using the provided script:
```bash

#!/bin/bash

[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.20.0/kind-linux-amd64
chmod +x ./kind
sudo cp ./kind /usr/local/bin/kind

VERSION="v1.30.0"
URL="https://dl.k8s.io/release/${VERSION}/bin/linux/amd64/kubectl"
INSTALL_DIR="/usr/local/bin"

curl -LO "$URL"
chmod +x kubectl
sudo mv kubectl $INSTALL_DIR/
kubectl version --client

rm -f kubectl
rm -rf kind

echo "kind & kubectl installation complete."
```


## 2. Installing docker
Install docker using the provided script:
```bash

#!/bin/bash

sudo apt-get update

sudo apt-get install docker.io

sudo usermod -aG docker $USER && newgrp docker  

echo "docker installation complete."
```

## 3. Setup KIND

```bash

#!/bin/bash

chmod +x ./kind

kind create cluster --name=tws-cluster --config=config-kind.yaml

echo "kind steup completed."
```