# ansible_add_use_to_host
1. Create ssh-key
  if you are root -> then        ssh-keygen -t rsa -C "alex@test"
2. Copy public key to your host  ssh-copy-id -i /home/alex/.ssh/id_rsa.pub alex@192.168.0.2
3. Try to enter   ssh 'alex@192.168.0.2'  , if you could not connect to the server without a password, you should press ctrl + d and try to connect with your user account alex@test:  ssh 'alex@192.168.0.2'

4.Then we add user "deploy" to our virtual-mashine 192.168.0.2 and give him NOPASSWD ALL. Autorization ONLY SSH-KAY
On the 192.168.0.2  ansible_ssh_private_key_file=/home/alex/.ssh/id_rsa we must write ip-address our mashine and PRIVATE SSH_KAY.
Then  ansible-playbook playbook.yml -i inventory_adduser_to_host -u alex -K

5.Install package {git, vim, mc, tmux, htop, curl, ntp}

ansible-playbook apt_install_package.yml -i inventory_adduser_to_host -u deploy
