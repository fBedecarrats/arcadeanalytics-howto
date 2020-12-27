
#  Create a Neo4J container with version 3.5.3
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
# Instanciate an Arcade Analytics

Run the following commands to download arcadeanalytics-recipes
```
# On linux, open the terminal, on Windows, open cmd
curl -LJO https://github.com/ArcadeData/arcadeanalytics-recipes/archive/master.zip 
unzip arcadeanalytics-recipes-master.zip
# Sous Windows, remplacer 'mv' par 'move'
mv arcadeanalytics-recipes-master arcadeanalytics-recipes
# Sous Windows, remplacer 'rm' par 'del'
rm arcadeanalytics-recipes-master.zip
```

Create the container
```
cd arcadeanalytics-recipes
# Specify the name you want after -p instead of "My_Name"
docker-compose -f recipes/arcade-standalone.yml -p "My_Name" up
```
Connect to Arcadeanalytics:
On the web browser, type http://localhost:8080 (http, not httpS).
Use the default logins: user = 'user', password = 'user' (change logins after the first use).

