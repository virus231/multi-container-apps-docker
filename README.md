# multi-container-apps-docker


### **Dockerizing the MongoDB Service** [![MongoDB](https://img.shields.io/badge/MongoDB-20232A?style=for-the-badge&logo=mongodb&logoColor=green)](https://github.com/virus231)
    1. docker run --name mongodb --rm -d -p 27017:27017 mongo
    2. cd backend => node app.js => CONNECTED

### **Dockerizing the Node App** [![Node.js](https://img.shields.io/badge/Node.js-20232A?style=for-the-badge&logo=nodejs&logoColor=green)] 
    1. cd backend
    2. docker build -t goals-node .
    3. docker run -d -p 3000:3000 goals-node
    4. docker run --name goals-backend --rm goals-node => ERROR: Failed
    5. localhost => host.docker.internal
    6. docker build -t goals-node .
    7. docker run --name goals-backend --rm -d -p 80:80 goals-node