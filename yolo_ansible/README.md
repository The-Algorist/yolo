# Ansible Deployment

## Overview
1. Configure Ansible provisioning in the Vagrantfile
2. Create a playbook.yaml file 
3. Create roles and define the following tasks separately:
   - server-configuration.(installs dependencies on remote server)
   - docker-install.(installs docker and docker-compose)
   - clone-yolo. (clones and runs the docker-compose.yaml file)
4. Test the application to ensure the containers are running in remote server and application is accesible on localhost.
5. Test for persistence

### 1. Configure Ansible provisioning in the Vagrantfile

- Run `vagrant init` on root direcory to initialize the Vagrantfile.
- Modify the Vagrantfile with instructions to set up the Virtual Box.
- ```yaml
    config.vm.provision "ansible" do |ansible|
    ansible.playbook = "yolo_ansible/playbook.yaml"
    ansible.verbose = "v"
    
  end
  
  ```
### 2. Create a `playbook.yml` file.
### 3. Create roles and define the following tasks separately:
- Create Roles
  - Create roles with each task as follows, which will generate different folders and modify `main.yml` for each task and `vars` files.
    - `ansible-galaxy init server-configuration`
    - `ansible-galaxy init docker-install`
    - `ansible-galaxy init clone-yolo`

Roles:
- `server-configuration`
- `docker-install`
- `clone-yolo`

### 4. Test the application to ensure the containers are running in remote server and application is accesible on localhost.

- Run `vagrant provision` to execute the playbook and set up Vagrant.
- Run `vagrant ssh` to log in to Vagrant.
- Execute `sudo docker ps -a` to verify running containers
- Test application by accessing `http://localhost:3000`


### 5. Test for persistence.