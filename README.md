# Sad Linux Server project

These are a couple (read, two) of Ansible automation playbooks which I used to configure and misconfigure Linux Ubuntu Server, later that server was used to test basic Linux knowledge of a candidates for a SysAdmin/DevOps/SRE role  

## Requirements  

We need Ansible installed on a local machine (tested with **Ansible 2.15.2**)  
We also need a server with root user and ssh key to access that server as a root user  

## Make server

Once we have a server with proper access make sure to update the inventory file *ansible/inventory/test_machines.ini* with adequate IP address. Also, check the files with variables *ansible/inventory/host_vars/candidate_vm/vars.yml* and secret variables *ansible/inventory/host_vars/candidate_vm/vault.yml* to make sure that you have all the necessary info regarding server setup, after that you can run following command to initially configure server  
`ansible-playbook ansible/playbook_make_server.yml --extra-vars 'hosts=candidate_vm' -i ansible/inventory/test_machines.ini -u root --private-key <path_to_the_root_user_private_key> --ask-vault-pass`  
(for this project, I have used *stefan5594* as a vault password. I know, I know this shouldn't be here, but it is a showcase project :man_shrugging:)

## Break server

Now that the server is properly configured, you are allowed to misconfigure it using following Ansible playbook  
`ansible-playbook ansible/playbook_break_server.yml --extra-vars 'hosts=candidate_vm' -i ansible/inventory/test_machines.ini -u root --private-key <path_to_the_root_user_private_key> --ask-vault-pass`  
