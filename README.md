# Bakery
DevOps Loft Bakery Onboarding Challenge

sudo apt install docker -y;
docker pull jenkins/jenkins;
docker network create jenkins;
docker volume create jenkins-docker-certs;
docker volume create jenkins-data;
docker container run --name jenkins-docker --rm --detach   --privileged --network jenkins --network-alias docker   --env DOCKER_TLS_CERTDIR=/certs   --volume jenkins-docker-certs:/certs/client   --volume jenkins-data:/var/jenkins_home   --publish 2376:2376 docker:dind;
docker container run --name jenkins --rm --detach   --network jenkins --env DOCKER_HOST=tcp://docker:2376   --env DOCKER_CERT_PATH=/certs/client --env DOCKER_TLS_VERIFY=1   --volume jenkins-data:/var/jenkins_home   --volume jenkins-docker-certs:/certs/client:ro  -p 11000:8080 jenkins/jenkins;
cat /var/lib/docker/volumes/jenkins-data/_data/secrets/initialAdminPassword;
** copy the password , login to http://127.0.0.1:11000/ , install suggested plugins and configure admin password ** 
** install maven integration plugin **
sudo apt install maven -y;
which mvn; #will result maven binary - copy the path jenkins -> manage -> global tool config -> maven
** fork https://github.com/deepak2717/HelloWorldMaven ** 
https://github.com/Michael-Masas/HelloWorldMaven






