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
sudo apt install docker-compose
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






