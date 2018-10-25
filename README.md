## Accessing MongoDB Data with REST

Example to connect in a MongoDB Server with [Spring Boot](https://spring.io/guides/gs/accessing-mongodb-data-rest/)

Using [Docker](https://hub.docker.com/_/mongo/).

**Setup**
```
# Use the oficial container
docker pull mongo
```

**Run mongodb server**
```
$ docker run --name mymongo -v [local-path]:/data/db -p 27017:27017 -d mongo
```

**Run**
```
$ mvn clean && mvn install
$ java -jar target/rest-api-mongodb-0.0.1.jar 
```

**Test**
```
$ mongo 
 > show dbs
 > use test
 > show collections
 > db.person.find()
```

Using [Postman](postman/) execute calls to localhost:8080
```
$ curl http://localhost:8080/people
$ curl -i -X POST -H "Content-Type:application/json" -d "{  \"firstName\" : \"Frodo\",  \"lastName\" : \"Baggins\" }"
$ curl http://localhost:8080/people
$ curl http://localhost:8080/people/search/findByLastName?name=Baggins
$ curl -X PUT -H "Content-Type:application/json" -d "{ \"firstName\": \"Bilbo\", \"lastName\": \"Baggins\" }" 
$ curl -X DELETE http://localhost:8080/people/{value}
```

Import de json file into Postman

**Stop mongodb server**
```
$ docker stop mymongo
```

**To-do**
- Write unit tests
- Write postman tests
- Create Docker compose
