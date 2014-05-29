#SSH
----
How to setup ssh pairs.

### Two authentication ways of SSH
#### 1. Password authentication
The local machine send the password to remote-host, remote-host verifies it and establish the connection.
#### 2. Key authentication
On local machine, you have two keys: `public key`(Others can hold it, like the remote-host) and `private key`(You should keep it secret). 

Local(A) stores both `public key` and `private key`;
Remote(B) stores only `private key`;

A wants to connect to B, and A need to prove he is A. A sends the `public key` to B. B stores a batch of public keys, and will try to match A's public key. Once matched, B will send A a `challenge` encoded by A's public key. A received the `challenge`, and decode by A's `private key`, send back the response to B. After B verifies the response, connection will be established. 

Usually, the `private key` is encrypted by a `passphrase`, so in local machine, you will need to input the `passphrase`, but this `passphrase` will not send out via Internet.

#### SSH usually have two versions: OPENSSH and SSH2

Check your ssh version:
```
[local-host]$ ssh -V
OpenSSH_5.0p1, OpenSSL 0.9.8g 19 Oct 2007

[remote-host]$ ssh -V
ssh: SSH Secure Shell 3.2.9.1 (non-commercial version) on i686-pc-linux-gnu
[remote-host]$ ls -l /usr/local/bin/ssh
lrwxrwxrwx  1 root root 4 Mar 10 22:04 /usr/local/bin/ssh -> ssh2
```

#### Connect remote from local

##### Local Side

**Case 1**: Your local ssh is **openssh**
Onlocal side, you need to create two keys: `public key` and `private key`:
```
[local-host]$ ssh-keygen -t dsa -b 1024 # dsa
[local-host]$ ssh-keygen -t rsa -b 1024 # rsa
```
It will generate two keys by default name : `id_dsa` and `id_dsa.pub`

**Case 2**: Your local ssh is **ssh2**
Still haven't tried.

##### Remote Side
On remote sied, you need to store the public key generated on local machine.

**Case 1**: Your remote-host ssh is **openssh**
Under `~/.ssh` create one file `authorized_keys`, and copy your content of public key into it. 
```
[remote-host] mkdir .ssh && cd .ssh
[remote-host] touch authorized_keys
[remote-host] # copy the content into it.
```

**Case 2**: Your remote-host ssh is **ssh2**
On local side, you need to convert openssh public key to ssh public key:
```
[local] ssh-keygen -e -f ~/.ssh/id_rsa.pub > ~/.ssh/id_rsa_ssh2.pub
```
User ~/.ssh2 folder, copy your `public key` (file:`id_dsa_ssh2.pub`) to this folder, create the `authentiation` file, edit it as `Key id_dsa_ssh2.pub`
```
[reomote] echo 'Key id_dsa_ssh2.pub' > authentiation
```