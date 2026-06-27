readme


ansible --version
echo -e "[local]\nlocalhost ansible_connection=local"> hosts.ini
ansible-inventory -i hosts.ini --list
nano setup.yml

---
- name: Basic Server Setup
hosts: local
become: yes
tasks:
- name: Update apt cache
apt:
update_cache: yes
- name: Install curl
apt:
name: curl
state: present

ansible-playbook -i hosts.ini setup.yml
curl --version
