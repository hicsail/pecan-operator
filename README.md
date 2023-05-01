# Commands to recreate

# Install Operator SDK
https://sdk.operatorframework.io/docs/installation/

To install on MacOS run:
```
brew install operator-sdk
```

# Install Ansible

Install Dependencies
This will take a while, continue to the next steps while it runs. 
```
brew install git python gnu-tar
pip3 install virtualenv
```

Create a virtual environment
```
virtualenv ~/ansible
source ~/ansible/bin/activate
```

Install Ansible
```
pip install setuptools_rust wheel kubernetes
pip install --upgrade pip
pip install ansible
```

Create a new Operator
```
operator-sdk init --plugins=ansible --domain sail.codes
```

Create a new API
```
operator-sdk create api --group pecan --version v1 --kind Pecan --generate-role
```

Create new tasks for the operator
In roles/pecan/tasks/main.yml

Check the chart version of pecan by downloading this file:
https://opensource.ncsa.illinois.edu/charts/index.yaml


## Install kubernetes.core Ansible Galaxy Collection
```bash
ansible-galaxy collection install kubernetes.core
```
### Upgrade kubernetes.core Ansible Galaxy Collection if necessary
```bash
ansible-galaxy collection install kubernetes.core -U
```

---
Create a new playbook to install pecan
Created ./pecan.yml
namespace is Openshift Project Name

---
Create a role for rabbitMQ
In config/rbac/role.yaml
Add the following:
```
  - apiGroups:
      - rbac.authorization.k8s.io
    resources:
      - roles
    verbs:
      - create
      - delete
      - get
      - list
      - patch
      - update
      - watch
```


Run the playbook
```
ansible-playbook pecan.yml
```