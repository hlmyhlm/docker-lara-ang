Docker project test with Laravel backend, Angular Front End, MySQL DB

The project incorporates services like Php, MySQL, 
Phpmyadmin, Redis, and Nginx. In the Laravel realm, 
Made use of features such as JWT Token for authentication, 
GraphQL for data querying, Redis Queue for queue processing, 
Observer and Event Listener for data listening and event management, 
Commands for custom commands, 
Faker for generating fake data, 
and Model and Migrations for data structures. 
On the Angular side: including Router for page navigation, 
Guards for authorization, 
Http Interceptor for handling HTTP requests, 
Toastr for notifications, data management through services, 
storage operations, and Bootstrap integration. 
Throughout the project, prioritized the 
SOLID, KISS, and DRY principles


**Installation;**

Before running Docker, copy either the .env.docker or .env.local file in the 'backend' folder to 
the .env file. We will proceed using the .env.docker file.

---
Verify that the API_URL variable in 
the 'app.constants.ts' file located in the 'projects/client/src/app/configs' directory 
is set to 'http://backend.test/api'.

---

Locate the 'hosts' file on your computer and 
add the following lines to it. On Windows systems, 
this file can be found in the directory C:\Windows\System32\drivers\etc.

    127.0.0.1 backend.test
    127.0.0.1 client.test

---

Run Docker by typing the command "docker-compose up --build -d" 
in the directory where the docker-compose.yml file is located.
Make sure docker-compose is install (if CLI is used)
    docker-compose up --build -d

---

Make sure that all services are running as shown in the image below
![image Docker-Services](images/docker-services.PNG)

---

Check the services from your terminal. 
To do this, simply run the command "docker ps". 
This will list the services and their status

    docker ps

---

Test access the PHPMyAdmin panel running on port 8081 through 
the "myadmin" service. After entering the username and password 
as "root" for both, you will log in as an administrator. Then, follow these steps:

- *Create a new database with the name mentioned in the .env file
 as MYSQL_DATABASE, which in this case is "db_test".*

(Note: Ignore this: In the .env.local file, PostgreSQL has been set as the database, please take note)
 
---

We need to connect to the terminal of the service with the "Container ID" 
of the "php7" service among those listed with "docker ps"

For example, let's assume the 
Container ID is "39979863cb2b." To connect to the terminal 
of this service, you should run the command "docker exec -it 39979863cb2b bash"


    docker exec -it 39979863cb2b bash
    

(Note: You can also connect by typing the first 3 characters. "docker exec -it 399 bash" will work as well.)

    
    docker exec -it 399 bash
    

![image Docker-PS](images/docker-ps.PNG)
---
Run "composer install"

Run the command "cd backend && php artisan migrate" to execute 
the migrations for the database.


    cd backend && php artisan migrate

(Note: While you are in the "backend" directory, 
you can also use the commands "php artisan queue:work" 
and "php artisan schedule:run" for queue processing and running scheduled tasks.)


    php artisan queue:work
    php artisan schedule:run


Note:
Run "php artisan storage:link" and also check folder permission if there is "storage permission" error when first time "http://backend.test" is accessed:
    To do this in root folder:

    chown -R www-data:www-data *



Sample Pictures;
-
***GraphQL*** (localhost:8000/graphql-playground)

![image GraphQL](images/graphql.PNG)

***Postman***

![image Postman](images/postman.PNG)

Project Pictures;
-

***Login***
![image Login](images/login.PNG)

***Register***
![image Register](images/register.PNG)

***Dashboard***
![image Dashboard](images/dashboard.PNG)

***Posts***
![image Post-List](images/post-list.PNG)

***Comments***
![image Comment-List](images/comment-list.PNG)

