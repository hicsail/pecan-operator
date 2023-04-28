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
pip install setuptools_rust wheel
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

Create a new Role
```
