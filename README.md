參考： https://medium.com/@knoldus/how-to-install-docker-on-rhel-using-ansible-role-62728c098351

# install_docker_AWS_EC2_RHEL_Ansible
install docker on AWS EC2 RHEL using Ansible playbook

### 1. Create a directory
$ mkdir ansible && cd ansible

### 2. Create a role
$ ansible-galaxy init install_docker，會長得像這樣：
<img src="image/截圖 2024-05-19 上午10.31.02.png" width="70%" height="70%">

### 3. Write yaml files
$ cd tasks/
在task底下新增五個yml file:
installPackages.yml
addRepo.yml
installDocker.yml 
addUser.yml
main.yml

在 vars 底下新增一個yml file:
main.yml

install_docker資料夾外，新增docker.yml

### 4. 設定
$ vi /etc/ansible/hosts (inventory file)，寫下EC2的相關資訊:
[webserver]
wordpress ansible_host=3.238.27.181 ansible_user='ec2-user' ansible_ssh_private_key_file=/Users/zhonganqing/.ssh/wca4a-0514.pem

 ### 5. run playbook:
 $ ansible-playbook docker.yml --ask-become-pass

執行成功畫面：
<img src="image/截圖 2024-05-19 上午10.12.08.png" width="70%" height="70%">

到EC2確認畫面：
 $ docker -v


<img src="image/截圖 2024-05-19 上午10.22.20.png" width="70%" height="70%">

