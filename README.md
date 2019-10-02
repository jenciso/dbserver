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
echo 'ansible ALL=(ALL) NOPASSWD: ALL' > /etc/sudoers.d/ansible
```

Criar uma chave ssh

```
su - ansible
ssh-keygen
```


![image](https://i.imgur.com/ZZ85rr6.png)

