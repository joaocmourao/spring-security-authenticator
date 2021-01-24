# spring-security-authenticator

<h1>Prerequisites:</h1>
->mysql database

<p>Using docker to get mysql database:</p>
<p>1-get mysql docker container:
docker run -p 3306:3306 --name=mysql57 -d mysql/mysql-server:5.7</p>
<p>2-get generated password</p>
docker logs mysql57 2>&1 | grep GENERATED
<p>3-connect mysql client using the password</p>
docker exec -it mysql57 mysql -uroot -p
<p>4-change root password</p>
ALTER USER 'root'@'localhost' IDENTIFIED BY 'NEW_USER_PASSWORD';
FLUSH PRIVILEGES;
<p>5-set the host</p>
update mysql.user set host = '%' where user='root';
<p>6-restart container</p>
docker restart mysql57

You will now be able to connect to mysql running on docker using mysql workbench client.

<p>Before using this project you must create new users to test it:<p>
  insert  into `user`(`id`,`is_active`,`password`,`roles`,`user_name`)
values (1,1,'user@123','ROLE_USER','user'),
(2,1,'admin@123','ROLE_ADMIN','admin');
