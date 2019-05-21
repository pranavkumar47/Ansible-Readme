# current version and status of the ansible application 
ansible --vertion 

# list all the hosts configured in your environment 
ansible all --list-hosts

# list the content of the host file 
cat /etc/ansible/hosts 

# install the telnet package on the server 
ansible webserver -s -m yum -a 'pkg=telnet state=installed update_cache=ture'

# display system facts and use filter 
ansible webserver -m setup -a 'filter=ans*ipv4*'

# use shell command to check lynx is installed or not 
anisble webserver -m shell -a 'yum list | grep lynx'

# ansible command that display the last ten lines of output 
ansible webserver -m shell -a 'tail -n 10 /var/log/dmesg'

mkdir playbooks 
cd playbooks 
touch deploy2019.yml 

# install lynx and check telnet is installed or not

- hosts: appaserver
  task:
  - name: install lynx on app server 
    yum: pkg=lynx state=installed update_cache=true 
  - name: querying for telnet install 
    yum: pkg=telnet state=present update_cache=true

# run the playbook 
ansible-playbook -s deploy2019.yml

# check the ansible logfile 
tail /var/log/ansible.log 

ansible all --list-hosts
cat /etc/ansible/hosts
mkdir playbooks
cd playbooks
vim firstplaybook.yml

# playbook for 
#-- force use of ssh connectin and 
#-- always run the playbook as the user 'test' & 
#-- runt the playbook as SUDO user by default 
#-- do not use the setup module to gather facts from system during execution 

--- # YAML playbook for ansilble 
- hosts: webserver 
  user: test 
  sudo: yes
  connection: ssh
  gather-facts: no 
 
# run the playbook

ansible-playbook firstplaybook.yml

