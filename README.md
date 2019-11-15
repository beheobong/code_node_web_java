# code_node

### 1. Error: EACCES: permission denied, access '/usr/local/lib/node_modules'
- https://stackoverflow.com/a/51024493/10819917

### 2. Uploading files to a Google Cloud server with SFTP using FileZilla:
- https://www.youtube.com/watch?v=SZLXP5k2tb8

### 3. MongoDB Click to Deploy on Google Cloud Platform
- https://www.youtube.com/watch?v=H5gF9fjNMF8

```sh
CODE CENTOS

rm -rf /home/huynhphongchau/nhadatdn-server

sudo npm install --unsafe-perm -g

curl -sL https://rpm.nodesource.com/setup_10.x | sudo bash -

sudo yum install -y nodejs

sudo yum install git

git clone https://gitlab.com/huynhphongchau/nhadatdn-server.git

git pull origin master

sudo npm install -g --unsafe-perm=true --allow-root

sudo PORT=80 npm start

forever start -c "sudo PORT=80 npm start" ./

https://ssh.cloud.google.com/projects/nhadatdn/zones/asia-east1-a/instances/nhadatdn-vps-1?authuser=0&hl=en_US&projectNumber=478345864763

connect to VPS
cd ~/.ssh
ssh -i gc_rsa chau_736331@35.221.154.112
```
