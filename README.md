# project-ansible

## This is how to deploy dynatrace on kubernetes (or Rancher) using Ansible

### Prerequisite:
- ansible-playbook   (ansible-playbook --version)
- python >= 2.7
- openshift >= 0.6  (pip install openshift)
- PyYAML >= 3.11  (pip install PyYAML)

- check that you have k8s config file in ~/.kube to access k8s   
    -- to check : (kubectl config get-contexts)

### Deploying dynatrace

```
cd dynatrace/playbooks
sudo ansible-playbook ./dynatrace-oneagent-operator-playbook.yaml
```



### Check that it is installed sucessfully
```
kubectl get po -n dynatrace
kubectl get customresourcedefinitions.apiextensions.k8s.io oneagents.dynatrace.com
```

![alt text](https://github.com/Eslamanwar/project-ansible/blob/master/dynatrace/images/ansible1.png?raw=true)








# ArgoCD

## This is how to deploy Argocd on kubernetes (or Rancher) using Ansible

### Prerequisite:
- ansible-playbook   (ansible-playbook --version)
- python >= 2.7
- openshift >= 0.6  (pip install openshift)
- PyYAML >= 3.11  (pip install PyYAML)

- check that you have k8s config file in ~/.kube to access k8s   
    -- to check : (kubectl config get-contexts)


### Deploying Argocd

```
cd argocd/playbooks

sudo ansible-playbook argocd-playbook.yaml --extra-vars "argocd_version=v1.4.2 argocd_url=example.com gitlab_url=gitlab.com gitlab_application_secret=secret gitlab_application_id=121212121212 gitlab_deploy_private_key=asas argocd_values_file=values.yaml"

```


### Check that Argocd is installed sucessfully
```
kubectl get po -n argocd

## To open Argocd 
kubectl -n argocd port-forward svc/argocd-server 7000:80
## Then Browse to localhost:7000

```

![alt text](https://github.com/Eslamanwar/project-ansible/blob/master/argocd/images/argo1.png?raw=true)
![alt text](https://github.com/Eslamanwar/project-ansible/blob/master/argocd/images/argo2.png?raw=true)








