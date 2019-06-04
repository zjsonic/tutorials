# Mongodb Basic

High Level Steps:

- Installation
- Start
- Connection
- Create
- Security

## Installation

- version: MongoDB Community Editon
- Platform: Ubuntu 18.04 MacOS

### Installation on MacOS

```bash
brew tap mongodb/brew # to tap the MongoDB Homebrew Tap
brew install mongodb-community@4.0 # Install MongoDB
brew uninstall mongodb-community@4.0
```

Configuration File: `/usr/local/etc/mongod.conf`:

```bash
systemLog:
  destination: file
  path: /usr/local/var/log/mongodb/mongo.log
  logAppend: true
storage:
  dbPath: /usr/local/var/mongodb
net:
  bindIp: 127.0.0.1
```



### Installation on Ubuntu 18.04

```bash
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 9DA31620334BD75D9DCB49F368818C72E52529D4
echo "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.0.list
sudo apt-get update
sudo apt-get install -y mongodb-org

```

Configure file: `/etc/mongod.conf`

```bash
storage:
    dbPath: /var/lib/mongodb
systemLog:  
    logAppend: true
    path: /var/log/mongodb/mongod.log

net:
    port: 27107
    bindIp: 127.0.0.1

security:
    authorization: 'enabled'
```


### check the version

```bash
mongodb --version # check the version of mongodb
```

## Start

### Start MongoDB on MacOS

```bash
mongod --config /usr/local/etc/mongod.conf # run mongodb
brew services start mongodb-community@4.0 # run mongodb as a mac service
brew services stop mongodb-community@4.0
```

### Start MongoDB on Ubuntu

```bash
sudo service mongod status # check the service's status
sudo service mongod stop # stop the mongodb server anytime
sudo service mongod start # start the mongodb server
sudo service mongod restart # restart the mongodb server
```

### Start MongoDB without access control
 
```base
mongod --port 27017 --dbpath /var/lib/mongodb
```

## Connection

If you try to access the mongo shell by simply typing `mongo` in the terminal. You will get through but won't be able to access any database. You need to use your created users to access the databases.

### Connection with The Mongo Shell

- The mongo shell is an interactive js interface to MongoDB. You can use the mongo shell to query and update data as well as perform administrative operations.
- The mongo shell is a component of the MongoDB. Once you have installed the MongoDB and started it, you can connect the mongo shell to  the running mongodb instance.
- `which mongo`: look for the location of the mongo 

### Connect MongoDB with a Full URI

macOS\ubuntu:

```bash
mongo -u 'username' xxx.xxx.xx.xx./admin -p
```

### Connect MongoDB without a Full URI(未验证)

macOS\ubuntu:

```bash
mongo -u 'username' --port 27017 --host xxx.xxx.xx.xx -p 
```

## Create

Create 'admin' user

```sql
use admin;
db.createUser({
    user: "admin",
    pwd: "123456",
    roles: [
        { role: "userAdminAnyDatabase", db: "admin" },
        { role: "dbAdminAnyDatabase", db: "admin" },
        { role: "readWriteAnyDatabase", db: "admin" }
    ]
})

```

creat a DB user

```sql
db.createUser({
    user: 'user1',
    pwd: '123456',
    roles: [
        { role: 'userAdmin', db: 'testdb' },
        { role: 'dbAdmin', db: 'testdb' },
        { role: 'readWrite', db: 'testdb' }
    ]
})
```

Create database 'testdb'

```sql
use testdb; --'testdb' will not be present in database list till you insert something into it. 
db.movie.insert({"name":"tutorials point"})
```

## Security

### Firewall

```bash
sudo ufw enable # enable the firewall
sudo ufw disable # disable the firewall
sudo ufw allow 27017 # allow port 27017
sudo ufw allow from another_server_ip/32 to any port 27017 # In most cases,MongoDB should be accessed from certain trusted server hosting an app. 27017:mongodb's port
sudo nano /etc/mongodb.conf # open the config file and bind your server ip: bind_ip = 127.0.0.1,server_ip
sudo netstat -plntu # check that mongodb has been started on the port 27017
sudo systemctl restart mongodb # restart the mongodb server

```
MongoDB is now listening for remote connections, but anyone can access it. 

### Authorization

Open the MongoDB config file:

```bash
udo vim /etc/mongod.conf
```

In this file add the following lines:

```bash
security:
    authorization: 'enabled'
```

This will tell mongodb that whenever it starts up next, it needs to enforce database access control using the roles we created in the previous step.

## Remote

Open the MongoDB config file:

```bash
udo vim /etc/mongod.conf
```

Change the `bindIp` from `127.0.0.1` to `0.0.0.0`

```
# network interfaces
net:
    port: 27017
    bindIp: 0.0.0.0   # means allow connections from any ip address #default value is 127.0.0.1 
```

However, we are still accessing the mongo shell from within the vultr instance. We havn't tried connecting remotely. To be able to do that,change the network settings of your vultr instance.

Open up network port on the vultr instance

MongoDB uses port 27107 for all connections by default.
So, let's open up that port. You can go to the network settings of your vultr console and 
open up `inbound` and `outbound` traffic on port 27107

```
sudo iptables -A INPUT -p tcp --destination-port 27017 -m state --state NEW,ESTABLISHED -j ACCEPT
sudo iptables -A OUTPUT  -p tcp --source-port 27017 -m state --state ESTABLISHED -j ACCEPT
```

## 参考

- 教程:![https://www.tutorialspoint.com/mongodb/mongodb_create_collection.htm](https://www.tutorialspoint.com/mongodb/mongodb_create_collection.htm)
- config firewall: ![https://www.digitalocean.com/community/tutorials/how-to-install-mongodb-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-install-mongodb-on-ubuntu-18-04)
- ![Setting up and connecting to a remote MongoDB database](https://medium.com/founding-ithaka/setting-up-and-connecting-to-a-remote-mongodb-database-5df754a4da89)