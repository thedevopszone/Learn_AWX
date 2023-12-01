# Learn AWX

## Install AWX In Docker

```
sudo apt update && sudo apt upgrade -y
```

Install docker
```
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh

sudo groupadd docker
sudo usermod -aG docker $USER
```


Install compose
```
sudo apt install python3-pip
pip install docker-compose
```


Install Ansible
```
sudo apt install ansible
```

```
sudo apt install nodejs npm 
npm install npm --global
sudo apt install python3-pip git pwgen
pip3 install docker-compose==1.25.0
```

```
wget https://github.com/ansible/awx/archive/17.1.0.zip
sudo apt install unzip
unzip 17.1.0.zip
cd awx-17.1.0/
cd installer
pwgen -N 1 -s 30
BuQHwx6eHoPgZqwUk79XoYOWIW8zoT
```

```
vi inventory
#on the bottom add 
admin_user=tmundt
admin_password=P@ssw0rd
secret_key=<key_just_created_with_pwgen>
ansible-playbook -i inventory install.yml
docker ps
http://<IP>:80
With user pass from inventory
```


## Install AWX In Podman

```
sudo apt update && sudo apt upgrade -y
```


Install Podman
```
sudo apt install -y podman 
```



Install compose
```
sudo apt install podman-compose
```

sudo apt install docker-compose
Install Ansible

sudo apt install ansible
sudo apt install nodejs npm 
npm install npm --global
sudo apt install python3-pip git pwgen
pip3 install docker-compose==1.25.0
wget https://github.com/ansible/awx/archive/17.1.0.zip
sudo apt install unzip
unzip 17.1.0.zip
cd awx-17.1.0/
cd installer
pwgen -N 1 -s 30
BuQHwx6eHoPgZqwUk79XoYOWIW8zoT
vi inventory
#on the bottom add 
admin_user=tmundt
admin_password=P@ssw0rd
secret_key=<key_just_created_with_pwgen>
ansible-playbook -i inventory install.yml
docker ps
http://<IP>:80
With user pass from inventory




## Install AWX In Kubernetes

```
git clone https://github.com/ansible/awx-operator.git
cd awx-operator
git checkout 0.19.0
export NAMESPACE=awx
make deploy
kubectl get po -n awx

https://github.com/Ompragash/awx-deploy
git clone https://github.com/Ompragash/awx-deploy.git
cd awx-deploy
AWX_WEB_FQDN="ec2-18-216-51-154.us-east-2.compute.amazonaws.com"
openssl req -x509 -nodes -days 3650 -newkey rsa:2048 -out tls-cert.pem -keyout tls-key.pem -subj "/CN=${AWX_WEB_FQDN}" -addext "subjectAltName = DNS:${AWX_WEB_FQDN}"

kubectl -n awx create secret tls awx-secret-tls --cert=./tls-cert.pem --key=./tls-key.pem --dry-run=client -o yaml

Copy the hole output

vi 01-secret.yaml

Add
---
And paste here

kubectl apply -f 01-secret.yaml

mkdir -p /data/postgres
mkdir -p /data/projects

chmod 755 /data/postgres
chown 1000:0 /data/postgres

kubectl apply -f 02-pv.yaml

kubectl apply -f 03-pvc.yaml
kubectl apply -f 04-awx.yaml

kubectl -n awx logs -f deployments/awx-operator-controller-manager -c awx-manager
kubectl get awx -n awx
kubectl get all -n awx

https://<dns>
user: admin
pass: Look at the secret file
vi 01-secret.yaml  awx-admin-password: AnsibleRocks



```




