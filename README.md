## Centos Networking

Editar  /etc/sysconfig/network-scripts/ifcfg-enp0s3

```
ONBOOT=yes
IPADDR=10.0.5.11
PREFIX=24
GATEWAY=10.0.5.1
DNS1=10.0.5.1
```
## Criando usuario ansible

```
useradd ansible
passwd ansible
```

Criar o seguinte arquivo

```
cd /etc/sudoers.d
echo 'ansible ALL=(ALL) NOPASSWD: ALL' > /etc/sudoers.d/ansible
```

Criar uma chave ssh

```
su - ansible
ssh-keygen
```


![image](https://i.imgur.com/ZZ85rr6.png)

Acessar via Putty ou ssh usando a TCP port 2211
```
ssh -p 2211 root@localhost
```

![image2](https://i.imgur.com/a8n12S5.png)


## To provision

```
ansible -m shell -a "echo kube-master.10.0.5.31.xip.io > /etc/hostname" -i inventory centos
ansible -m shell -a "sed -i 's/^IPADDR=10.0.5.11$/IPADDR=10.0.5.31/' /etc/sysconfig/network-scripts/ifcfg-enp0s3" -i inventory centos
ansible -m shell -a "reboot" -i inventory centos
```

