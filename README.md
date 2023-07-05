# elasticsearch-docker
Docker setup for Elasticsearch New VERSION=7.16.1 with TLS and Nginx Setup <br>
This is a Docker setup for the Elastic And Kibana stack, useful to  TEST And Production Environement <br>

The following Docker containers are available

Elasticsearch instance (7.16.1), a single cluster, accessible from domain without ports
And Kibana instance  (7.16.1)

After complete setup  Elasticsearch and Kibana will be available in internet as

https://elastic.example.com <br>
https://kibana.example.com




Setup

1.This repository provides a Docker configuration to set up a local test environment or production environment.

2.Install Docker for your OS if not already present
alternatively use a VM or install Elasticsearch locally on your system
Most examples require only a single Elasticsearch instance, therefore it's sufficient to start one instance.

**NOTE**: user server certs as per your company use(you need crt and key file), update the filename in docker compose file

3.Before build run this command in linux server to set the vm max memory <br>

```sudo sysctl -w vm.max_map_count=262144```
4.To create the ca crt run <br>
```docker-compose -f create-certs.yml run --rm create_certs```
5.To build elastic and kibana run

```docker-compose up -d --build```

You can see elastic container up but kibana is showing elastic user authentication not found

6.Run this command to generate the elastic user password,

```docker exec es01 /bin/bash -c "bin/elasticsearch-setup-passwords auto --batch --url https://localhost:9200"```

After generating the password update the  password in docker compose file and do <br>
```docker-compose restart or docker-compose down and docker compose up -d```


7.Hoping Nginx is installed in the server <br>

Copy the Nginx-elastic and kibana conf to the nginx conf directory 



