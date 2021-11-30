The purpose of this project is to use docker to quickly deploy

First clone https://github.com/PluskitOfficial/nt_container
Then enter the nt_container directory and clone in turn:
- https://github.com/PluskitOfficial/nt_s_common
- https://github.com/PluskitOfficial/nt_s_tools
- https://github.com/PluskitOfficial/nt_web

The final directory structure is as follows:

nt_container/
- nt_s_common/
- nt_s_tools/
- nt_web/
- dockerfiles/
- docker-compose.yml


## step 1
Create a local network:
`docker create network dev_network`

## step 2
Since the project needs to use redis and mysql, you need to create a new `dev.env` file in the nt_container directory, and then write the following:
```
# redis config
REDIS_HOST=192.168.0.1
REDIS_PORT=6379
REDIS_PASSWORD=redis-pwd

# mysql config
MYSQL_HOST=192.168.0.2
MYSQL_USER=root
MYSQL_PASSWORD=mysql-pwd
MYSQL_PORT=3306

# server config
SERVER_API=http://nt-s-tools:10010
SERVER_TOOLS=http://nt-s-tools:10010

# data api config 
XM_HOST=https://api.atpool.com
XM_APP_ID=your app id
XM_APP_SECRET=your app secret
```

## step 3
Use the docker command to start the service: 
`docker-compose up -d`

Then you can visit  http://127.0.0.1:22001 

