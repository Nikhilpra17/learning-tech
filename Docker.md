// creating dockerFile which is use to make docker image

FROM node:20

WORKDIR /myapp

COPY . /myapp       // or COPY . .  or ./myapp.py . 

RUN npm install

EXPOSE 3000

CMD ["npm", "start"]        // CMD ["python", "myap.py"]


// docker build .  (Run on terminal to create the image from the docker file)

// docker build -t mywebapp:01 . (Creating image using the name under -t tag with version )

// docker rmi nameOrTag (remove image)

// docker tag myOlderName:tag newName:01 (change name of the image)

// docker image ls (show all images)

// docker ps (process status)

// docker run imageId (running the container from the Docker)

// docker stop imageId

// docker run -d -p 3000:5173 2fhkfhwjh3342kbh (running the container from the Docker)
             local Port : container Port


// docker run -d --rm -p 3000:5173 2fhkfhwjh3342kbh (will automatically removed after stopped)

// docker run --name "mywebPage" -d --rm -p 3000:5173 2fhkfhwjh3342kbh (manually giving name to container)

// docker run -it 2fhkfhwjh3342kbh (running the container in interactive terminal)

// docker login

// docker run -d --rm -v myvolume:/myapp/ 2fhkfhwjh3342kbh  (creating volume so that it can store the data)

// docker run --rm -v /users/project/server.txt:/myapp/server.txt --rm 2fhkfhwjh3342kbh (bind mount file from local to container folder)
// it help in live updating,uses during live development 

// .dockerignore

// connceting the local database 
host = "host.docker.internal"

//communicating between two container

// docker network
docker network create my-net (creating network)

// docker run -d --env MYSQL_ROOT_PASSWORD="root" --env MYSQL_DATABASE="userInfo" --name mysqldb --network my-net mysql

//docker-compose.yml
services:
    mysqldb: 
        image: "mysql:latest"
        environment:
            - MYSQL_ROOT_PASSWORD="root"
            - MYSQL_DATABASE="userInfo"
        conatiner_name: "mysqldb"

docker-compose up -d
docker-compose down




