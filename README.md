# Konecta-Kubernetes
Konecta-K8s tasks.

_Pre-task setup:

-created 3 AWS instances: 1 ( Control plane ), 2 ( worker nodes ).

-Attached a SG to all 3 instances with the following rules:

Allow SSH (port 22) from your IP

Allow all traffic within the cluster (nodes should communicate freely)

Allow API server (port 6443) from your IP / your vpc CIDR (optional for external access)

Allow NodePort range (30000-32767) for external service access


_Performed these steps on all 3 instances:

Update System and Install Dependencies

Disable Swap: Kubernetes requires swap to be disabled

Load Kernel Modules and Configure sysctl

Install Container Runtime (Containerd)

Install Kubernetes Packages


_Initializing the Control Plane node:

Command: sudo kubeadm init --pod-network-cidr=192.168.0.0/16

![k8s1](https://github.com/user-attachments/assets/2c582e13-689e-4383-ac77-4ae402f3fcd5)

-Set up kubectl for the current user:

Command: mkdir -p $HOME/.kube

sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config

sudo chown $(id -u):$(id -g) $HOME/.kube/config

-Install the network plugin (on the control plane)

Command: kubectl create -f https://raw.githubusercontent.com/projectcalico/calico/v3.29.2/manifests/tigera-operator.yaml

kubectl create -f https://raw.githubusercontent.com/projectcalico/calico/v3.29.2/manifests/custom-resources.yaml

Join the worker nodes to the cluster:

Command: sudo kubeadm join 172.31.77.207:6443 --token ji2d6l.n7ow5m6rouyq3koh \
        --discovery-token-ca-cert-hash sha256:ba2a1a0e37aef7e83a21b8c8b75a7c1c5a275185bafacaf39007ccd9edb15b52

![k8s2](https://github.com/user-attachments/assets/b2325fdb-0309-486e-8f4c-69a6cb0400c1)

![k8s3](https://github.com/user-attachments/assets/9e116a4d-ea50-4cd9-83a1-dcb404b25867)



