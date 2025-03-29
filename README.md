# MongoDocker
docker network create mongoCluster



docker run -d --rm -p 27017:27017 --name mongo10 --network mongoCluster mongodb/mongodb-community-server:latest --replSet myReplicaSet --bind_ip localhost,mongo10

docker run -d --rm -p 27018:27017 --name mongo20 --network mongoCluster mongodb/mongodb-community-server:latest --replSet myReplicaSet --bind_ip localhost,mongo20

docker run -d --rm -p 27019:27017 --name mongo30 --network mongoCluster mongodb/mongodb-community-server:latest --replSet myReplicaSet --bind_ip localhost,mongo30

docker run -d --rm -p 27020:27017 --name mongo40 --network mongoCluster mongodb/mongodb-community-server:latest --replSet myReplicaSet --bind_ip localhost,mongo40

docker run -d --rm -p 27021:27017 --name mongo50 --network mongoCluster mongodb/mongodb-community-server:latest --replSet myReplicaSet --bind_ip localhost,mongo50



docker exec -it mongo40 mongosh


db.runCommand({hello:1})


rs.initiate({ _id: "myReplicaSet", members:[{_id:0, host: "mongo10"}, {_id:1, host: "mongo20"}, {_id:3, host: "mongo30"}, {_id:4, host: "mongo40"}, {_id:5, host: "mongo50"}]})


exit



docker exec -it mongo10 mongosh --eval "rs.status()"



mongodb://127.0.0.1:27017/?directConnection=true&serverSelectionTimeoutMS=2000&appName=mongosh+2.3.8



rs.isMaster().primary



use CorporeSystem



db.cliente.insertOne({codigo:1, nome: "Ana Maria"});
db.cliente.insertOne({codigo:2, nome: "Maria Jose"});
db.cliente.insertOne({codigo:3, nome: "Jose Silva"});
db.cliente.insertOne({codigo:4, nome: "Luis Souza"});
db.cliente.insertOne({codigo:5, nome: "Fernanda Silva"});



db.cliente.find()



docker stop mongo10



docker exec -it mongo20 mongosh --eval "rs.status()"


db.cliente.insertOne({codigo:6, nome: "Teresa Maria"});


mongodb://127.0.0.1:27021/?directConnection=true&serverSelectionTimeoutMS=2000&appName=mongosh+2.4.2


use CorporeSystem



db.cliente.findOne()



db.cliente.insertOne({codigo:7, nome: "Joao Cardoso"});



docker run -d --rm -p 27017:27017 --name mongo10 --network mongoCluster mongodb/mongodb-community-server:latest --replSet myReplicaSet --bind_ip localhost,mongo10



docker exec -it mongo50 mongosh --eval "rs.status()"



docker stop mongo20


docker exec -it mongo30 mongosh --eval "rs.status()"


db.cliente.insertOne({codigo:6, nome: "Teresa Maria"});



db.cliente.findOne()



db.cliente.insertOne({codigo:8, nome: "Carlos Souza"});


docker run -d --rm -p 27018:27017 --name mongo20 --network mongoCluster mongodb/mongodb-community-server:latest --replSet myReplicaSet --bind_ip localhost,mongo20



docker exec -it mongo50 mongosh --eval "rs.status()"
