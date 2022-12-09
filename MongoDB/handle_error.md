# Problems
## Unable to start MongoDB services
### Descrpition
- The file ownership is changed to root or admin. The current permission isn't high enough to enable the service
### Solutions
- 1. deleting the mongod sock file
```
sudo rm -rf /tmp/mongodb-27017.sock
sudo systemctl start mongod
```
- 2. Change file ownership
```
chown -R mongodb:mongodb /var/lib/mongodb 
chown mongodb:mongodb /tmp/mongodb-27017.sock 
sudo service mongod restart
```
