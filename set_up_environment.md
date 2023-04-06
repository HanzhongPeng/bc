# ubuntu环境设置

## 系统版本查看
`lsb_release -a`

No LSB modules are available.

Distributor ID:	Ubuntu

Description:	Ubuntu 20.04.6 LTS

Release:	20.04

Codename:	focal



## root用户设置
### 设置root密码
`sudo -i`

[sudo] password for penghz: 

`passwd`

New password: 

Retype new password: 

passwd: password updated successfully

## 设置网络代理
### 设置vmware网络模式
在vmware中，设置虚拟机的网络模式为桥接模式，并且勾选“复制物理网络连接状态”

### ubuntu网路代理设置
在本机clash代理的情况下，设置ubuntu系统代理

在pc的terminal中用

`ipconfig`

查看本机ip地址，子网掩码和网关
![](markdown_img/ipconfig.png)
把ubuntu的网络设置中的代理设置为手动，并且填入本机的代理地址和端口
![](markdown_img/ubuntu_ipconfig.png)
把proxy设置为手动，然后把本机ip和端口号7890填入到代理中





在ubuntu的terminal中用


# Fabric环境设置
```
sudo apt-get install git curl docker-compose -y

# Make sure the Docker daemon is running.
sudo systemctl start docker

# Add your user to the Docker group.
sudo usermod -a -G docker <username>

# Check version numbers  
docker --version
docker-compose --version
  
# Optional: If you want the Docker daemon to start when the system starts, use the following:
sudo systemctl enable docker
```
## 预先工作
https://hyperledger-fabric.readthedocs.io/en/latest/prereqs.html
## Fabric例程
`curl -sSL https://raw.githubusercontent.com/hyperledger/fabric/main/scripts/bootstrap.sh| bash -s`

Clone hyperledger/fabric-samples repo

===> Changing directory to fabric-samples  
===> Checking out v2.4.9 of hyperledger/fabric-samples
fatal: detected dubious ownership in repository at '/home/penghz/Desktop/fabric_bc/test/fabric-samples'
To add an exception for this directory, call:

	git config --global --add safe.directory /home/penghz/Desktop/fabric_bc/test/fabric-samples

Pull Hyperledger Fabric binaries

===> Downloading version 2.4.9 platform specific fabric binaries
===> Downloading:  https://github.com/hyperledger/fabric/releases/download/v2.4.9/hyperledger-fabric-linux-amd64-2.4.9.tar.gz
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
100 86.0M  100 86.0M    0     0   593k      0  0:02:28  0:02:28 --:--:--  584k
==> Done.
===> Downloading version 1.5.5 platform specific fabric-ca-client binary
===> Downloading:  https://github.com/hyperledger/fabric-ca/releases/download/v1.5.5/hyperledger-fabric-ca-linux-amd64-1.5.5.tar.gz
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:--  0:00:01 --:--:--     0
100 29.4M  100 29.4M    0     0   582k      0  0:00:51  0:00:51 --:--:--  586k
==> Done.

Pull Hyperledger Fabric docker images

FABRIC_IMAGES: peer orderer ccenv tools baseos
===> Pulling fabric Images
====>  docker.io/hyperledger/fabric-peer:2.4.9
2.4.9: Pulling from hyperledger/fabric-peer
ef5531b6e74e: Pull complete 
cb6adad689bd: Pull complete 
010602cca7ea: Pull complete 
dadcffad5b31: Pull complete 
3b71f3b82217: Pull complete 
9917d15b0b5a: Pull complete 
6a2c93fa3f95: Pull complete 
Digest: sha256:6ff36af21eb1e0b74f09187a6090c27c42d82b33aa0404bcf94558217e1dfba2
Status: Downloaded newer image for hyperledger/fabric-peer:2.4.9
docker.io/hyperledger/fabric-peer:2.4.9
====>  docker.io/hyperledger/fabric-orderer:2.4.9
2.4.9: Pulling from hyperledger/fabric-orderer
ef5531b6e74e: Already exists 
cb6adad689bd: Already exists 
010602cca7ea: Already exists 
44d81e4543ec: Pull complete 
9c0a7cb5c6af: Pull complete 
275371067d0a: Pull complete 
d90823f8c566: Pull complete 
Digest: sha256:6ec3fe59ea55b690aaab6c69e5e23da5dc99afda2f046116ed296b395e4d47d1
Status: Downloaded newer image for hyperledger/fabric-orderer:2.4.9
docker.io/hyperledger/fabric-orderer:2.4.9
====>  docker.io/hyperledger/fabric-ccenv:2.4.9
2.4.9: Pulling from hyperledger/fabric-ccenv
ca7dd9ec2225: Pull complete 
c41ae7ad2b39: Pull complete 
eda8cd824576: Pull complete 
d71a49e0649a: Pull complete 
d34b692b3ee4: Pull complete 
66044e0a0724: Pull complete 
d974a502e7a7: Pull complete 
4fc4ce450dbd: Pull complete 
Digest: sha256:b23821060701e9713c4714f337f691b0a736a9312a9360e0886f3acf1df210bc
Status: Downloaded newer image for hyperledger/fabric-ccenv:2.4.9
docker.io/hyperledger/fabric-ccenv:2.4.9
====>  docker.io/hyperledger/fabric-tools:2.4.9
2.4.9: Pulling from hyperledger/fabric-tools
ca7dd9ec2225: Already exists 
c41ae7ad2b39: Already exists 
eda8cd824576: Already exists 
d71a49e0649a: Already exists 
e918dcca351a: Pull complete 
8c49fb870a8c: Pull complete 
aa900656510d: Pull complete 
Digest: sha256:b1194f509085e0fe622355d119fbb8dfef8b2d78954eabd7d221a39fc90bb850
Status: Downloaded newer image for hyperledger/fabric-tools:2.4.9
docker.io/hyperledger/fabric-tools:2.4.9
====>  docker.io/hyperledger/fabric-baseos:2.4.9
2.4.9: Pulling from hyperledger/fabric-baseos
ef5531b6e74e: Already exists 
cb6adad689bd: Already exists 
bed8f466ba67: Pull complete 
Digest: sha256:b86dc8040a48c4dc9df5a9cb309a40ffaaf3984f5cbfe555c00ecf4d02c52ef9
Status: Downloaded newer image for hyperledger/fabric-baseos:2.4.9
docker.io/hyperledger/fabric-baseos:2.4.9
===> Pulling fabric ca Image
====>  docker.io/hyperledger/fabric-ca:1.5.5
1.5.5: Pulling from hyperledger/fabric-ca
2408cc74d12b: Pull complete 
979557f40538: Pull complete 
b3bcd28c0311: Pull complete 
Digest: sha256:f93cd9f32702c3a6b9cb305d75bed5edd884cae0674374fd7c26467bf6a0ed9b
Status: Downloaded newer image for hyperledger/fabric-ca:1.5.5
docker.io/hyperledger/fabric-ca:1.5.5
===> List out hyperledger docker images
hyperledger/fabric-tools     2.4       6997a3225d8b   4 weeks ago    490MB
hyperledger/fabric-tools     2.4.9     6997a3225d8b   4 weeks ago    490MB
hyperledger/fabric-tools     latest    6997a3225d8b   4 weeks ago    490MB
hyperledger/fabric-peer      2.4       b1c5352410a0   4 weeks ago    64.2MB
hyperledger/fabric-peer      2.4.9     b1c5352410a0   4 weeks ago    64.2MB
hyperledger/fabric-peer      latest    b1c5352410a0   4 weeks ago    64.2MB
hyperledger/fabric-orderer   2.4       d64956fd66bb   4 weeks ago    36.7MB
hyperledger/fabric-orderer   2.4.9     d64956fd66bb   4 weeks ago    36.7MB
hyperledger/fabric-orderer   latest    d64956fd66bb   4 weeks ago    36.7MB
hyperledger/fabric-ccenv     2.4       7557f03b34a9   4 weeks ago    521MB
hyperledger/fabric-ccenv     2.4.9     7557f03b34a9   4 weeks ago    521MB
hyperledger/fabric-ccenv     latest    7557f03b34a9   4 weeks ago    521MB
hyperledger/fabric-baseos    2.4       0792904ee001   4 weeks ago    6.8MB
hyperledger/fabric-baseos    2.4.9     0792904ee001   4 weeks ago    6.8MB
hyperledger/fabric-baseos    latest    0792904ee001   4 weeks ago    6.8MB
hyperledger/fabric-ca        1.5       93f19fa873cb   9 months ago   76.5MB
hyperledger/fabric-ca        1.5.5     93f19fa873cb   9 months ago   76.5MB
hyperledger/fabric-ca        latest    93f19fa873cb   9 months ago   76.5MB




# 遇到的问题

## ubuntu网络按钮消失
(1) 打开终端，输入sudo service network-manager stop  
(2) sudo rm /var/lib/NetworkManager/NetworkManager.state  
(3) sudo service network-manager start