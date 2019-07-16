# Gobarber Backend

## Extensions

### yarn add:

  * express
  * sucrase (dev)
  * nodemon (dev)

### express

  Creates the server inside the `app.js` file and listen to a port inside the `server.js` file

### sucrase 

  Adds latest code style features to node. To use it, create a `nodemon.json` file inside the root folder
  with the following object:

    {
      "execMap": {
        "js": "sucrase-node"
      }
    }
  
  This will make syntax such as `import` and `export default` understandable by node (like babel)

### nodemon

  Will watch your files and detect changes, automatically restarting your local server.
  Add the following object to the `package.json` file

    "scripts": {
      "dev": "nodemon src/server.js"
    }

  To start the app, run `yarn dev` 

  ## Docker

  Creates isolated containers to facilitate and improve development

  * Image -> tools we can run inside containers (ex: postgreSQL, mySQL, etc)
  * Container -> instance of an image (ex: 3 postgreSQL on the databases running separatly)
  * Docker Registry -> Docker Hub
  * Docker file -> recipe of an image

  [Installation site](https://docs.docker.com/install)

  If the tutorial on the site doesn't work , do:

    sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu xenial stable"
    sudo apt-get update
    apt-cache search docker-ce
    sudo apt-get install docker-ce docker-ce-cli containerd.io

  To check:

    sudo docker run hello-world

  [Post install on linux](https://docs.docker.com/install/linux/linux-postinstall/)

  If tutorial doesn't work (like in my case), do:

    sudo groupadd docker
    sudo usermod -a -G docker $USER

  Restart computer

  run `docker run hello-world` without `sudo`


  ### Install postgres
  
  run `docker run --name postgres -e POSTGRES_PASSWORD=docker -p 5432:5432 -d postgres`

    -d [docker instance name]
    -p [your_port:dockers_port]


  ### Docker commands:

  `docker ps` -> show all running dockers
  
  `docker ps -a` -> shol all dockers
  
  `docker container rm [CONTAINER ID] ` -> remove container


## Sequelize

### ORM

  * Tables become models

  * Migrations 
    * versioning of databases
    * ordenated by dates
    * Never edited, only new ones get created
    * Each mifration deals with only one table

  * Seeds
    * Creates fake data for **developing purposes only**

### MVC

  Structuring folders and files to keep responsabilities separate

  * Model

    * Holds the abstraction of the database, meaning that it holds the information for the tables


  * Controller

    * Business rules. Where requests go. Returns jsons to client. One for each entity. Only the five methods: index, show, store, update, delete

  * View

    * Holds info about what the end user will see. Not existent in REST APIs

# JWT -> Json Web Token -> User authentication

Estrutura:

    Headers.Payload.Assinatura