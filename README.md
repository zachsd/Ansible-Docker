Ansible-Docker
=========

This roles will docker-ce on supported platforms

Requirements
------------
A supported linux distribution, the roles follows the installation guide from the docker website. 
* https://docs.docker.com/install/

Supported Distributions: 
- Debian: 9+
- Ubuntu: 16.04+
- Fedora: 24+
- CentOS: 7
- RHEL: 7

Role Variables
--------------
To change the version of docker that is installed update the following variables, for example to get the latest avaiable package remvoe the version number and change the state to latest
```yaml
    # Fedora / CentOS / RHEL
    docker_ce_el:
      - name: docker-ce
        state: latest
    
    # Debian / Ubuntu
    docker_ce_debian:
      - name: containerd.io
        state: latest     
```
Default values are: 
```yaml
    # Fedora / CentOS / RHEL
    docker_ce_el:
      - name: docker-ce-19.03.4
        state: present
      - name: docker-ce-cli-19.03.4
        state: present
      - name: containerd.io-1.2.10
        state: present

    # Debian / Ubuntu
    docker_ce_debian:
      - name: containerd.io=1.2.10-3
        state: present
      - name: "docker-ce=5:19.03.4~3-0~{{ ansible_distribution|lower }}-{{ ansible_distribution_release }}"
        state: present
```

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:
```yaml
    - hosts: docker
      become: true
      roles:
         - ansible-docker
```         

License
-------

BSD

Author Information
------------------

Zachary Davis