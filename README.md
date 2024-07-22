# Wordpress-using-Docker
#Dockerizing the Wordpress site

Initialize the docker using

    systemctl start docker

Firstly create a folder wordpress-site and enter it using;

    mkdir wordpress-site && cd wordpress-site

This will put you in the folder you just created. We are now ready to get our Docker Compose file setup!!

Enter the folder and paste the below code;;

    vi wordpress-site

    version: ‘3’
    services:
    db:
    image: mariadb:10.5
    volumes:
      - db_data:/var/lib/mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: <your-root-password>
      MYSQL_DATABASE: <your-database-name>
      MYSQL_USER: <your-user-name>
      MYSQL_PASSWORD: <your-user-password>
  
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
      WORDPRESS_DB_USER: <your-db-user>
      WORDPRESS_DB_PASSWORD: <your-db-password>
      WORDPRESS_DB_NAME: <your-database-name>
      volumes:
      db_data:

Exit the code section by Esc+Shift+;   -----

Now, all you have to do is run the below command ;

    docker-compose up

Once it's done visit the--->>>  localhost:8000  
in your web browser and land on the default Wordpress setup page.

    docker-compose up

Once it's done visit the--->>>  localhost:8000  
in your web browser and land on the default Wordpress setup page.

![Screenshot 2024-07-22 161205](https://github.com/user-attachments/assets/ecc4e346-87c7-4ca9-b6d3-0884a72e121a)


