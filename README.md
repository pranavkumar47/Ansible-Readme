# current version and status of the ansible application 
ansible --vertion 

# list all the hosts configured in your environment 
ansible all --list-hosts

# list the content of the host file 
cat /etc/ansible/hosts 

# install the telnet package on the server 
ansible webserver -s -m yum -a 'pkg=telnet state=installed update_cache=ture'

# 1. display system facts and use filter 
ansible webserver -m setup -a 'filter=ans*ipv4*'

# 1. use shell command to check lynx is installed or not 
anisble webserver -m shell -a 'yum list | grep lynx'

# 1. 