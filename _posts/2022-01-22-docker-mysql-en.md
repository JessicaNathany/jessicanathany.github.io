---
layout: post

title: "How to create database MySQL with Docker"

date: 2022-01-22

lang: en

cover: "/assets/img/docker-mysql.jpg"

excerpt: "I'll show how to create a local MySQL database with Docker on your Windows. It is necessary to have the latest version of Docker installed on your machine."

tags: [docker, mysql]
---


## Introduction

In this article I'm going to show how to create a local MySQL database with Docker on your Windows. It is necessary to have the latest version of Docker installed on your machine.

### 1st step: Download the MySQL image

Let's download the latest MySQL image to the Docker hub, type the following command below:

```bash
docker pull mysql/mysql-server
```

### 2nd step: Execute the container

Let's execute the container for the image that we downloaded. At first, we won't configure environment variables, at the moment just execute MySQL for default users without a password. Before executing the command, you can create a directory with the name mysql. Write the command below in your terminal.

Note: create only the directory C:/mysql by default, MySQL needs to have the folder */var/lib/mysql, this directory is where MySQL will save your database.*

Write the command below

```bash
docker run -e MYSQL_ALLOW_EMPTY_PASSWORD=yes -v C:/mysql:/var/lib/mysql mysql
```

<br />
<div align="center">
  <img src="/assets/img/docker-mysql1.jpg" alt="imagem artigo cloudflare sobre SSL" style="max-width: 400px; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
</div>
<br />

<br />

<div align="center">
  <img src="/assets/img/docker-mysql2.jpg" alt="imagem artigo cloudflare sobre SSL" style="max-width: 400px; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
</div>
<br />

### 3rd step: Getting the container's IP

To discover the container IP, write the command docker container ls to verify the containers that are running and copy the ID of the container, using the command below

```bash
docker container inspect ID_CONTAINER
```

<div align="center">
  <img src="/assets/img/docker-mysql3.jpg" alt="imagem artigo cloudflare sobre SSL" style="max-width: 400px; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
</div>
<br />


### 4th step: Access database from container

To access the database through the container, we need to go inside the container, so write the command below

```bash
docker exec -it ID_CONTAINER
```
<div align="center">
  <img src="/assets/img/docker-mysql4.jpg" alt="imagem artigo cloudflare sobre SSL" style="max-width: 400px; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
</div>
<br />

<div align="center">
  <img src="/assets/img/docker-mysql5.jpg" alt="imagem artigo cloudflare sobre SSL" style="max-width: 400px; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
</div>
<br />

Done. We have a MySQL database in a Docker container. Now you can create your database and tables.

<div align="center">
  <img src="/assets/img/docker-mysql6.jpg" alt="imagem artigo cloudflare sobre SSL" style="max-width: 400px; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
</div>
<br />

### Conclusion

This is a simple example for you to create a database with Docker. Of course in this example I created a simple database, but you can configure user and password in your database.

Write it down so you don't forget.
