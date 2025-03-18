# Konecta-Kubernetes
Konecta-K8s tasks.

Pre-task setup:

created 3 AWS instances: 1 ( Control plane ), 2 ( worker nodes ).

Attached a SG to all 3 instances with the following rules:

Allow SSH (port 22) from your IP

Allow all traffic within the cluster (nodes should communicate freely)

Allow API server (port 6443) from your IP (optional for external access)

Allow NodePort range (30000-32767) for external service access


Performed these steps on all 3 instances:

Update System and Install Dependencies

Disable Swap: Kubernetes requires swap to be disabled

Load Kernel Modules and Configure sysctl

Install Container Runtime (Containerd)

Install Kubernetes Packages


Initializing the Control Plane node:















