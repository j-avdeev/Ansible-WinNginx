
### Ansible test project to install NGINX on Windows

#### Prerequisites
* Ansible Control node
* Windows-machine accessbile from Ansible Control node by WinRM
#### Run 
``$ cd ansible-webserver-setup`` \
``$ ansible-playbook -i hosts.ini --ask-vault-pass ./playbooks/generate_certs.yml`` \
``$ ansible-playbook -i hosts.ini --ask-vault-pass ./playbooks/install_nginx.yml`` \
``$ ansible-playbook -i hosts.ini --ask-vault-pass ./playbooks/configure_nginx.yml`` \
``$ ansible-playbook -i hosts.ini --ask-vault-pass ./playbooks/setup_firewall.yml`` \
to test \
``$ ansible-playbook -i hosts.ini --ask-vault-pass ./playbooks/nginx_check.yml`` 
#### Full Task Description

Test Assignment: Setting Up a Web Server on Windows Using Ansible \
Goal: \
Configure an Nginx web server on a Windows host using Ansible, including generating self-signed certificates, installing the necessary certificates on the system, configuring Nginx to work over HTTPS, and ensuring secrets management using Ansible Vault. \
Steps:
 1. Generate Self-Signed Certificates: \
 ◦ Generate a root self-signed certificate (CA certificate). \
 ◦ Generate a server certificate signed by the root certificate. \
 ◦ Install the root certificate in the "Trusted Root Certification Authorities" of the local machine on the Windows host.
 2. Install and Configure Nginx as a Service: \
 ◦ Install Nginx on the Windows host using WinSW (Windows Service Wrapper) to manage Nginx as a service. \
 ◦ Add necessary firewall permissions for Nginx to allow incoming connections on HTTP and HTTPS ports. \
 3. Configure Nginx to Work Over HTTPS: \
 ◦ Configure Nginx to use the previously created certificates to ensure the web server works over HTTPS. \
 4. Secrets Management: \
 ◦ Use Ansible Vault to securely store and manage sensitive data such as passwords and private keys. \
Expected Result: \
After completing all steps, Nginx should be installed and running as a service on the Windows host, configured to work over HTTPS using self-signed certificates. Secrets should be securely managed using Ansible Vault. \
Additional Requirements: \
 • Store the results in a GitHub repository. \
 • Include a README file with all prerequisites and a link to the repository. \
This task ensures a secure and automated setup of a web server with proper management of sensitive information.

#### Troubleshooting
* Check if WinRM works \
``winrm get winrm/config/Service``
* Check if WinRM + hosts.ini are correct \
``ansible -i hosts.ini -m win_ping DESKTOP-P8D82BI -u Administrator --ask-pass``
* Remove nginx service \
``PS Stop-Service -Name nginx``
``PS sc.exe delete nginx``
