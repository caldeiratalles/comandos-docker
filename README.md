# comandos-docker
Selecione no canto superior direito desse quadro para visualisar como código ícone <>
PROMETHEUS///////////////////PROMETHEUS///////////////////
docker run -d --name prometheus -p 9292:9292 -v /tmp/prometheus/prometheus.yml:/etc/prometheus/prometheus.yml prom/prometheus
JENKINS//////////////////////JENKINS//////////////////////
docker run -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts-jdk11
MYSQL////////////////////////MYSQL////////////////////////
docker run --name=mysql-docker -p3306:3306 -v mysql-volume:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 -d mysql/mysql-server:latest 
Problemas ao conectar com o mysql workbench?
docker logs mysql-docker 2>&1 | grep GENERATED
docker exec -it mysql-docker mysql -u root -p
update mysql.user set host = '%' where user='root';
quit;
docker restart mysql-docker
Agora tente conectar no mysql workbench
IBMMQ/////////////////////////////////IBMMQ///////////////
docker run --env LICENSE=accept --env MQ_QMGR_NAME=QM1 --volume qm1data:/mnt/mqm --publish 1414:1414 --publish 9443:9443 --detach --env MQ_APP_PASSWORD=passw0rd --name QM1 ibmcom/mq:latest
