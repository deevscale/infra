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

3. Start & Stop
    

    chmod 777 -R scripts/*     

4. install kubectl


    snap install kubectl --classic

5. Create namespaces


    kubectl create namespace development

6. Configure kubectl ([source][5])


    cd ~/.kube
    microk8s config > config
    kubectl config use-context microk8s
    
    kubectl config set-context --current --namespace=development

7. Enable MetalLB ([source][6])


    microk8s enable metallb:10.152.1.0
    kubectl apply -f metallb-custom-address-pool.yml



## Useful commands:
    

get all microk8s running services

    kubectl get all --all-namespaces

get microk8s dashboard

    microk8s dashboard-proxy


docker image run

    sudo docker run -p 5432:5432 -e POSTGRES_PASSWORD=12345 deevscale/principal-db

sh into pod

    kubectl exec -it <pod_name> -- sh

watch pods:

    kubectl get pods -n development -w

[1]: <https://www.markdownguide.org/basic-syntax/>
[2]: <https://ubuntu.com/tutorials/install-a-local-kubernetes-with-microk8s>
[3]: <https://github.com/canonical/microk8s>
[4]: <https://blog.antosubash.com/posts/deploy-docker-registry-and-postgres-database-in-micro-k8s>
[5]: <https://anaisurl.com/kubernetes-kubectl-microk8s/>
[6]: <https://microk8s.io/docs/addon-metallb>