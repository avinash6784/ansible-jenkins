# Ansible Role: Jenkins [Ansible Playbook Role To Install Jenkins]

Install Jenkins, a distributed version control system, on any RHEL/CentOS Linux system.

## Requirements

None.

## Role Variables
```yml

# Jenkins vars
jenkins_dest: /opt/jenkins
jenkins_lib: /var/lib/jenkins
port: 8081
prefix: '"--prefix=/jenkins/"'
jenkins:
  cli_dest: '{{ jenkins_dest }}/jenkins-cli.jar' # Jenkins CLI destination
  updates_dest: '{{ jenkins_dest }}/updates_jenkins.json' # Jenkins updates file
jenkins_api_url: "http://localhost:{{ port }}{{ prefix }}"
jenkins_cli_cmd: "java -jar {{ jenkins.cli_dest }} -s {{ jenkins_api_url }}"
java_home: /opt/jdk1.8.0_111

```

## Dependencies

This role depends on avinash6784.oracle-java role. This is configured for ansible-galaxy install in requirements.yml.

**NOTE**: Requirements are installed as virtual user avinash6784 (avinash6784.oracle-java).

Be sure to install required roles with
```
ansible-galaxy install --role-file requirements.yml
```

## Usage and Example Playbook

Install from Ansible Galaxy
```
$ ansible-galaxy install avinash6784.jenkins
```
Or download manually
```
$ git clone https://github.com/avinash6784/ansible-jenkins.git 
```
The code should reside in the roles directory of ansible ( See ansible documentation for more information on roles ), in a folder jenkins.

## Run the playbook

First create a playbook including the git role, naming it jenkins.yml.
```yml
- name: Install Jenkins
  hosts: jenkins
  become: true
  roles:
    - jenkins
    
$ ansible-playbook -i hosts jenkins.yml
```

## Author Informations

This role was created by [Avinash Pawar](http://devopstechie.com).
