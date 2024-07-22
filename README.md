#  Wordpress-using-Docker  

#  Prerequisites
I assume you have installed Docker and it is running.  
See the [Docker website](https://www.docker.com/get-started/#h_installation) for installation instructions.
Hope you know how to create the folder and edit it.

#  Build
Steps to initialize wordpress using docker    
1.Clone this repo   

        https://github.com/kanishkdw/Wordpress-using-Docker.git

2.Change the wordpress directory path Wordpress-using-Docker

         cd Wordpress-using-Docker
   
   
3.Open the docker-compose.yml file and update with your actual db user and password values.


    version: ‘3’
    services:
    db:
    image: mariadb:10.5
    volumes:
      - db_data:/var/lib/mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: <your-root-password>             #use your actual Mysql root password
      MYSQL_DATABASE: <your-database-name>                  #use your actual Mysql database name
      MYSQL_USER: <your-user-name>                          #use your actual Mysql username
      MYSQL_PASSWORD: <your-user-password>                  #use your actual Mysql user password
  
    wordpress:
    depends_on: db
    image: wordpress:latest
    ports:
      - “8000:80”
    restart: always
    volumes:
      - ./wordpress:/var/www/html/
    environment:
      WORDPRESS_DB_HOST: db:3306                    
      WORDPRESS_DB_USER: <your-db-user>                       #use your Db user
      WORDPRESS_DB_PASSWORD: <your-db-password>               #use your actual db password
      WORDPRESS_DB_NAME: <your-database-name>                 #use your actual database name          
      volumes:     
      db_data:

4.Initialize the docker compose  
        
        docker-compose up  

Once it's done you should be able to access the webpage via http://localhost:8000/wp-admin/index.php on your host machine  

        localhost:8000  


![Screenshot 2024-07-22 161205](https://github.com/user-attachments/assets/ecc4e346-87c7-4ca9-b6d3-0884a72e121a)


