# Cloud_21BCP387_Assignment
demo app - developing with Docker

This demo app shows a simple user profile app set up using

index.html with pure js and css styles
nodejs backend with express module
mongodb for data storage
All components are docker-based

Step 0: Get source code form the following repository:

```https://gitlab.com/nanuchi/developing-with-docker```

![Screenshot 2024-04-23 201923](https://github.com/GreenMask2003/21BCP387_Cloud_Assignment/assets/99289722/1bf81cad-cdfa-437f-8c82-6f2d33aa03ee)

With Docker
To start the application

Step 1: Create docker network

```docker network create mongo-network```

![Screenshot 2024-04-23 202208](https://github.com/GreenMask2003/21BCP387_Cloud_Assignment/assets/99289722/2b75cfc9-ce6a-47a4-a37c-d51887a5a4aa)

Step 2: start mongodb
```docker run -d -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=password --name mongodb --net mongo-network mongo```

![Screenshot 2024-04-23 202305](https://github.com/GreenMask2003/21BCP387_Cloud_Assignment/assets/99289722/856ce076-89db-4af7-8859-a362c8b52b76)

![Screenshot 2024-04-23 203811](https://github.com/GreenMask2003/21BCP387_Cloud_Assignment/assets/99289722/8b26eba4-2679-4579-b46f-01fae7b4e106)

Step 3: start mongo-express
```docker run -d -p 8081:8081 -e ME_CONFIG_MONGODB_ADMINUSERNAME=admin -e ME_CONFIG_MONGODB_ADMINPASSWORD=password --net mongo-network --name mongo-express -e ME_CONFIG_MONGODB_SERVER=mongodb mongo-express```
![Screenshot 2024-04-23 204549](https://github.com/GreenMask2003/21BCP387_Cloud_Assignment/assets/99289722/74d9fc40-d3ca-49ea-a3ef-994cfd355396)

NOTE: creating docker-network in optional. You can start both containers in a default network. In this case, just emit --net flag in docker run command
Step 4: open mongo-express from browser
```http://localhost:8081```
Step 5: create user-account db and users collection in mongo-express

![Screenshot 2024-04-23 210442](https://github.com/GreenMask2003/21BCP387_Cloud_Assignment/assets/99289722/3810eda4-9d72-48d7-a51d-be04dfb6b582)

![Screenshot 2024-04-23 210530](https://github.com/GreenMask2003/21BCP387_Cloud_Assignment/assets/99289722/ac6b7f11-50ec-4b11-aecf-2b9390d07c39)

Step 6: Start your nodejs application locally - go to app directory of project

```cd app npm install node server.js```
![Screenshot 2024-04-23 215105](https://github.com/GreenMask2003/21BCP387_Cloud_Assignment/assets/99289722/ac58b516-5082-41bd-b49f-f57f042a7d44)

Step 7: Access you nodejs application UI from browser

```http://localhost:3000```
![Screenshot 2024-04-23 215811](https://github.com/GreenMask2003/21BCP387_Cloud_Assignment/assets/99289722/2faa5b3e-881a-4039-925b-5b07a0293200)

![Screenshot 2024-04-23 220338](https://github.com/GreenMask2003/21BCP387_Cloud_Assignment/assets/99289722/9318c124-5d8c-440e-9ae2-76a660be8b45)

![Screenshot 2024-04-23 220506](https://github.com/GreenMask2003/21BCP387_Cloud_Assignment/assets/99289722/fe22a40e-aaea-467e-9481-2990fed756ea)

![Screenshot 2024-04-23 220726](https://github.com/GreenMask2003/21BCP387_Cloud_Assignment/assets/99289722/f7e58b1e-98fd-4c9f-a881-bf85b165d4da)

![Screenshot 2024-04-23 221345](https://github.com/GreenMask2003/21BCP387_Cloud_Assignment/assets/99289722/15b7fba2-8cd3-473e-aefa-7b4e2f1bb381)

With Docker Compose
To start the application
Step 1: start mongodb and mongo-express

docker-compose -f docker-compose.yaml up
You can access the mongo-express under localhost:8080 from your browser

Step 2: in mongo-express UI - create a new database "my-db"

Step 3: in mongo-express UI - create a new collection "users" in the database "my-db"

Step 4: start node server

```cd app npm install node server.js```
Step 5: access the nodejs application from browser

```http://localhost:3000```
To build a docker image from the application
```docker build -t my-app:1.0 .```       
The dot "." at the end of the command denotes location of the Dockerfile.


Finally, we will upload our project image to DockerHub for better containerization. For that, you need to log-in or create a new account on DockerHub if you don't have one.
To run a Three Tier Application, we need to run three Docker Containers simultaneously. So, it is necessary to run all these containers inside a network to avoid their interaction with other containers.

So, this is a step-by-step method to deploy your project using Docker. Thank you for reading my Blog!!
