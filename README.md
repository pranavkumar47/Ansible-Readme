# current version and status of the ansible application 
ansible --vertion 

# list all the hosts configured in your environment 
ansible all --list-hosts

# list the content of the host file 
cat /etc/ansible/hosts 

# install the telnet package on the server 
ansible webserver -s -m yum -a 'pkg=telnet state=installed update_cache=ture'

#testing somethjing  
hting
