
# Instanciate a Neo4J version
Create a container named "neo4j' specifying ports, neo4j version and password. Run it only once the first time.
```
docker run --rm -p 7474:7474 -p 7687:7687 -v $(pwd)/data:/data --env NEO4J_AUTH=neo4j/12345 --name neo4j neo4j:3.5.3
```
Then the neo4j client is accessible on the browser at: http://localhost:7474/browser/ 
To stop the container:
```
docker stop neo4j
```
To start the container again:

```
docker start neo4j
```
