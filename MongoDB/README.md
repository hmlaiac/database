# Catalog
## 1. Install MongoDB on Linux
- Follow Instructions below this link
- References: https://linuxize.com/post/how-to-install-mongodb-on-debian-10/

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