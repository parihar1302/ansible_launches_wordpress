
# wordpress_using_ansible


Reference : https://dotlayer.com/how-to-use-an-ansible-playbook-to-install-wordpress/

### 1. install ansilble on manage node and copying ssh key to target node :

#### on manage node
- `apt update `
- `apt install ansible`
- create a public-private keypair using `ssh-keygen -b 4096`
- copy the contents of the public key

#### on target node
- copy the public key content to ~/.ssh/authorized_keys on target machine
- run `service sshd restart`

#### on manage node
- try `ssh -i keyname username@ip.address.of.wordpress.server` to connect to the server 


### 2. Creating ansible playbook structure:

```
$ mkdir wordpress-playbook
$ cd wordpress-playbook
$ mkdir roles
$ touch hosts 
$ touch playbook.yml
```

### 3. Add hosts and initialize roles:

- `vi hosts` and add the following contents:
```
[wordpress]
wp_server_ip

```
- initialize all the roles using:
```
 $ cd roles 
 $ ansible-galaxy init server 
 $ ansible-galaxy init php 
 $ ansible-galaxy init mysql  
 $ ansible-galaxy init wordpress
```

This would be the structure by now:

each role folder has this structure:

#### 4. Editing the playbook and creating the roles:

