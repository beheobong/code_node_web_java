# code_node

### mở cổng vps: 
```sh
gcloud compute firewall-rules create <tên rule> --allow tcp:9999
```

### Tạo vps
- https://conduongkhoinghiep.vn/huong-dan-cach-tao-vps-tren-google-cloud/

### Login sv and install node 
- https://www.rosehosting.com/blog/how-to-install-node-js-and-npm-on-centos-7/

### Edit file:
```sh
Command Line
1. Right-click on the desktop and choose the "Open in Terminal" option from the menu that appears.
2. Type the cd command at the command prompt, followed by the name of directory that contains the text file:
cd directory_name

3. Type the vi command followed by the name of the file to open the file in Vi:
vi file_name.txt

4. Use the keyboard to navigate through the file. Press "j" to move the cursor down, "k" to move the cursor up, "h" to move the cursor left and "l" to move the cursor right.
5. Press the "i" key to insert text into the file.
6. Press the "Esc" key to return to normal mode to continue navigating through the file.
7. Type ":wq" on the keyboard to save and close the file.
```

### Set up basic
#### 1. install git
```sh
sudo yum install git
```
#### 2. install node
```sh
1. Login to your VPS via SSH
ssh user@vps_IP
2. Update the system and install necessary packages
yum install curl sudo
3. Install Node.js and npm from the NodeSource repository
We will install Node.js v6 LTS and npm from the NodeSource repository which depends on the EPEL repository being available.

To enable the EPEL repository on your CentOS 7 VPS, issue the following command:

sudo yum install epel-release
Once the EPEL repository is enabled run the following command to add the Node.js v6 LTS repository:

curl --silent --location https://rpm.nodesource.com/setup_6.x | sudo bash -
If you want to enable the Node.js v8 repository instead of the command above run the following command:

curl --silent --location https://rpm.nodesource.com/setup_8.x | sudo bash -
Once the NodeSource repository is enabled we can proceed with the Node.js v6 LTS and npm installation:

sudo yum install nodejs
4. Install build tools
To compile and install native add-ons from the npm repository we also need to install build tools:

sudo yum install gcc-c++ make
To verify if the Node.js installation was successful, issue the following command:

node -v
The output should be like the following:

v6.11.5
5. Verify npm installation
To verify if the npm installation was successful, issue the following command:

npm -v
The output should be like the following:

3.10.10
```

#### 3. install mongoDB

##### important:
```sh
gcloud auth login
gcloud compute firewall-rules create allow-mongodb --allow tcp:27017
```
 - https://www.digitalocean.com/community/tutorials/how-to-install-mongodb-on-centos-7
 - Tạo db và user
 ```sh
 use mydb
db.createUser({ user: 'myuser', pwd: 'mypassword', roles: ['readWrite'] })
 ```
 - Phương thức trong mongodb
 - https://www.tutorialspoint.com/mongodb/mongodb_create_database.htm
 - Config remote mongodb: https://medium.com/founding-ithaka/setting-up-and-connecting-to-a-remote-mongodb-database-5df754a4da89
 - connect from uri: https://stackoverflow.com/questions/45876403/mongodb-connect-locally-to-vps-database
 
 - remove mongo
 ```sh 
 1.Stop Mongo DB using -

sudo service mongod stop
or sudo systemctl stop mongod
2.Remove Packages using -

sudo yum erase $(rpm -qa | grep mongodb-org)
3.Remove Data Directories using -

sudo rm -r /var/log/mongodb
sudo rm -r /var/lib/mongo
```

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

### 4. deploy react web app "centos 7"
```sh
npm  run build
There are a few options here, by default if we use ‘Serve’ it will use port 5000;  This is run by calling the following :

serve -s build
```
