Pre-requisite - Setting up Ansible Master and Worker

Existing setup

Master : 192.168.56.100
Worker : 192.168.56.101

Master is also the Kubernetes Master node.

Generate ssh-keygen -t rsa. and the .pub key to authorised_key file on both master and worker

Step 1:

Setting up hosts file.  The host file /etc/hosts

192.168.56.100 evlab-master
192.168.56.101 evlab-worker


Step 2:

Setting up hosts file for ansible.  (As the excercise says to label the device as master1 and Worker1]

The host file entry will looks like in /etc/ansible/hosts

[masters]
master1

[workers]
worker1

Step 3:

Setting up user account to use for kubernetes deployment User_setup.yaml

As per the exercise, Deploy account should be used and securely used to deploy Kube cluster.

I’ve created this file to get the username at the run time. This is helpful to reuse the yml file for other purpose as well

Step 4: 

When this playbook runs, it uses the Deploy user account

Following are the list of tasks that this playbook performs

Kube-repos.yml

1. Disable swap
2. Remove swap entry to ensure it doesn’t come back on after server reboot
3. Installs Docker apt key
5. Add Docker repository 
6. Install Docker-CE
8. Add Google apt key

Step 5:

Kube-master.yml

1. Adding Kube group
2. Add Current user to the kube group
3. Initialise the cluster
4. create .kube directory
5. copy admin.conf to user's kube config
6. install Pod network


Step 6:

Kube-worker.yml

1. Get the join token from master1
2. Save the file to a .txt
3. Copy the file to worker1
4. Run the worker to Master node using the save file

