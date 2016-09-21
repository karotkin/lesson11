# lesson11

1.
To check how puppet single work we have to 

vim /etc/yum.repoes.d/nginx.repo

[nginx]
name=nginx repo
baseurl=http://nginx.org/packages/centos/$releasever/$basearch/
gpgcheck=0
enabled=1

And check our manifest

puppet manifest1.pp

nginx (pid  1393) is running...

2.
Add repositories at both sides of master and agent
sudo rpm -Uvh https://yum.puppetlabs.com/puppetlabs-release-pc1-el-6.noarch.rpm

Master:
sudo yum install -y puppetserver
and renew users session

Agent: 
vim /etc/hosts
add 192.168.33.6 master.minsk.epam.com
sudo yum install -y puppet-agent
and renew users session

3.
Master:
To handle issue with certs we have to work with:

puppet module install puppetlabs-ntp

And add manifest to our workspace 
vim /etc/puppetlabs/code/environments/production/manifests/case1.pp

Agent:

puppet agent --server servpuppet.minsk.epam.com -t

![](https://github.com/karotkin/lesson11/blob/master/1.png)

![](https://github.com/karotkin/lesson11/blob/master/2.png)
