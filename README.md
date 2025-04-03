# cdevops-jenkins
k8s lab to install jenkins and use it from github and gitea

TLDR;

```bash
ansible-playbook up.yaml
```

You may need some pre-requisites

1. Make sure that docker is running by doing `docker ps` until it shows 

```
CONTAINER ID   IMAGE                            COMMAND                  CREATED         STATUS         PORTS                             NAMES

```

2. run `ansible-playbook --version` to see if you have ansible. If not run:

```bash
bash <(curl -Ls https://raw.githubusercontent.com/conestogac-acsit/cdevops-bootstrap/refs/heads/main/bootstrap.sh)
```

3. run `kubectl get ns default` to see if you have a cluster. The expected result is:

```
NAME      STATUS   AGE
default   Active   29m
```

If you have another result try installing a k8s cluster:

```bash
bash <(curl -Ls https://raw.githubusercontent.com//conestogac-acsit/cdevops-bootstrap/refs/heads/main/k8s.sh)
```

Your job is to edit the up.yaml to add jenkins to your cluster and down.yaml to remove it. You will also need to expose jenkins with the ngrok ingress, as you did with the previous assignment.

### Points to Cover

## Marking

|Item|Out Of|
|--|--:|
|use [this article](https://www.digitalocean.com/community/tutorials/how-to-install-jenkins-on-kubernetes) and [this documentation](https://docs.ansible.com/ansible/latest/collections/kubernetes/core/k8s_module.html) to create an up.yaml that installs jenkins on your cluster|2|
|create a down.yaml that makes the resources created by up.yaml absent. (you will need to reverse the order)|2|
|Use [this article](https://www.jenkins.io/doc/tutorials/build-a-python-app-with-pyinstaller/) to create a 2nd repository containing a Jenkinsfile|2|
|push this repository to github and configure github to run the Jenkinsfile through the ngrok ingress|2|
|push this repository to gitea and configure gitea to run the jenkins file with the cluster ip|2|
|||
|total|10|

Submit links to all 3 repositories:

1. this repository with your up.yaml and down.yaml for running jenkins on your cluster.
2. your github repository with the fork from the article and a Jenkinsfile.
3. your gitea repository with the fork from the article and a Jenkinsfile, exposed with the ngrok ingress