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






















