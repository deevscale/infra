# intro

Infrastructure is consisted of k8s,docker
    
[formatting guide][1]

# Local
How to install microk8s: [guide][2]

1. Install through snap


    sudo snap install microk8s --classic

2. Enable add-ons


    microk8s enable dns
    microk8s enable dashboard
    microk8s enable storage


## Useful commands:


get all microk8s running services

    microk8s kubectl get all --all-namespaces
---
get microk8s dashboard

    microk8s dashboard-proxy
---
build docker image

    docker build -t deevscale/principal-db .



[1]: <https://www.markdownguide.org/basic-syntax/>
[2]: <https://ubuntu.com/tutorials/install-a-local-kubernetes-with-microk8s>
[3]: <https://github.com/canonical/microk8s>