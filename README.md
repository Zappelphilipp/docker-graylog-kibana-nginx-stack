# Graylog with Kibana behind nginx
This combination should be the best of both worlds: The ELK Stack vs Graylog. While the base is graylog Kibana is also connected to elasticsearch so you can use ether the graylog GUI or Kibana to extract data. Because Kibana doesn't have any usermanagement or password protection, it runs behind nginx as a reverse proxy to provide protection with .htpasswd. 

## How to start
First you need docker and docker-compose (oviously).

## Configuration
#### docker-compose.yml
If you want to use graylog on localhost, change nothing. In case you want to run it on a server it would be better to change *- GRAYLOG_WEB_ENDPOINT_URI=http://localhost:9000/api* to the desired IP-Adress.
THe default login credentials are: admin/admin. Change the SHA256 Hash to change the password. 

#### nginx/.htpasswd
Change the hash in case you want to change the password for the kibana-login mask. default login credentials are admin/admin

## Install
move into the directory where your docker-compose.yml is.
'''
docker-compose up
'''

## Run
connect to graylog: http://<IP>:9000
connect to kibana: http://<IP>:5601

I haven't changed the ports becaue this are the default ports for graylog/kibana. Change it in docker-compose.yml if you want.
