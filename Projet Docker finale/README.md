Transferer une base de données sur un Serveur de type TomCat

Les Creations des images
 •Creation des Dockerfiles
 
   FROM tomcat:8-jre8
   RUN apt-get update && apt-get install -y postgresql-9.5
   COPY ./dbproject.war /usr/local/tomcat/webapps/

   FROM postgres:9.5
   VOLUME /var/lib/postgresql/data
   COPY ./init-db.sql /docker-entrypoint-initdb.d/

 •Creation des images
   docker build -t mysql:2.0 sql

   docker build -t mytomcat:2.0 tomcat

 •Execution des images

   docker run -d -v dbdata:/var/lib/postgresql/data --name db mysql:2.0
   docker run -d --name mytomcat --link db -p 4224:8080 mytomcat:2.0

   
   #Rémy	#Razi	#Azelarab
   

