# multi-container-apps-docker


### **Dockerizing the MongoDB Service** [![MongoDB](https://img.shields.io/badge/MongoDB-20232A?style=for-the-badge&logo=mongodb&logoColor=green)](https://github.com/virus231)
    1. docker run --name mongodb --rm -d -p 27017:27017 mongo
    2. cd backend => node app.js => CONNECTED

### **Dockerizing the Node App** [![NodeJS](https://img.shields.io/badge/NodeJS-20232A?style=for-the-badge&logo=nodejs&logoColor=green)] 
    1. cd backend
    2. docker build -t goals-node .
    3. docker run -d -p 3000:3000 goals-node
    4. docker run --name goals-backend --rm goals-node => ERROR: Failed
    5. localhost => host.docker.internal
    6. docker build -t goals-node .
    7. docker run --name goals-backend --rm -d -p 80:80 goals-node

### **Moving the React SPA into a Container** [![ReactJS](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=bright)] 
    1. cd frontend
    2. docker build -t goals-react .
    3. docker run --name goals-frontend --rm -p 3000:3000 -it goals-react

### **Adding Docker Networks for Efficient Cross-Container Communication**
    1. docker network create goals-net
    2. docker network ls
    4. docker run --name mongodb --rm -d --network goals-net mongo
    5. docker run --name goals-backend --rm -d -p 80:80 --network goals-net goals-node  
    6. docker run --name goals-frontend --rm -p 3000:3000 - -network goals-net -it goals-react

### **Adding Data Persistence to MongoDB with Volumes**
    1. docker volume create data
    2. docker run --name mongodb --rm -d --network goals-net -v data:/data/db mongo
    3. docker run --name mongodb -v data:/data/db --rm -d --network goals-net -e MONGO_INITDB_ROOT_USERNAME=max -e MONGO_INITDB_ROOT_PASSWORD=secret mongo
    4. docker run --name goals-backend --rm -d -p 80:80 --network goals-net goals-node


