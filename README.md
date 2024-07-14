


ansible-playbook -i hosts.ini --ask-vault-pass ./playbooks/generate_certs.yml
ansible-playbook -i hosts.ini --ask-vault-pass ./playbooks/install_nginx.yml
ansible-playbook -i hosts.ini ./playbooks/configure_nginx.yml
ansible-playbook -i hosts.ini ./playbooks/setup_firewall.yml

ansible-vault create group_vars/my_vault.yml
ansible-vault edit my_vault.yml
ansible-ault view my_vault.yml

Encrypting Credentials:
$ ansible-vault encrypt_string 'your_password' --name 'ansible_password'

$ ansible-playbook --ask-vault-pass site.yml
--vault-password-file
