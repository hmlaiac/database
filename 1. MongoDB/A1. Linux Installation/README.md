# Catalog
## 1. Install MongoDB on Linux
- 1.2 Follow Instructions below this link
- 1.2 References: https://linuxize.com/post/how-to-install-mongodb-on-debian-10/
- 1.4 Input this command to activate command prompt of MongoDB
```
ubuntu:~$ mongo
```
- 1.3 Create Database Admin
```
db.createUser({
      user: "user1",
      pwd: "user1password",
      roles: [
                { role: "userAdmin", db: "sampledb" },
                { role: "dbAdmin",   db: "sampledb" },
                { role: "readWrite", db: "sampledb" }
             ]
  });
```

- 1.4 Create SuperUser for specific Database
```
db.createUser({ 
      user: "user1",
      pwd: "user1password",
      roles: [ 
                { role: "userAdminAnyDatabase", db: "admin" }, 
                { role: "readWriteAnyDatabase", db: "admin" }, 
                { role: "dbAdminAnyDatabase",   db: "admin" } 
             ] 
  });
```

- 1.5 Create User for specific Database
```
db.createUser(
{
user: 'username',
pwd: 'password',
roles: [{role: 'readWrite', db: 'safio'}]
}
);

```

## 2. Enable MongoDB Auth
- 2.1 Modify Configuration of Database
```
sudo vim /etc/mongod.conf
```

- 2.2 Change authorization to 'enabled'
```
security:
    authorization: 'enabled'
```

- 2.3 Enable all Ip address to access the database
```
# network interfaces
net:
    port: 27017
    bindIp: 0.0.0.0   #default value is 127.0.0.1
```

- 2.4 Restart and Reset Severice
```
sudo service mongod restart
```
- 2.5 Test Connection
```
# to access the admin database
ubuntu:~$ mongo -u admin -p myadminpassword 127.0.0.1/admin
# to access the other databases
ubuntu:~$ mongo -u user1 -p user1password 127.0.0.1/sampledb
```

## 3. Open up network port on the EC2 instance
- Different Cloud platforms may have different configurations
- Please set up your configurations depending on your platforms

## 4. Mongo Compass Connections
- mongodb://username:password@ip_address:port

## References:
- Install MongoDB on Debian:
- https://linuxize.com/post/how-to-install-mongodb-on-debian-10/
- Create account and network connection
- https://medium.com/founding-ithaka/setting-up-and-connecting-to-a-remote-mongodb-database-5df754a4da89
- MongoDB Open network tutorial
- https://docs.mongodb.com/manual/reference/connection-string/