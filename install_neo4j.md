Install Neo4J

```
docker run \
    --publish=7474:7474 --publish=7687:7687 \
    --volume=$HOME/neo4j/data:/data \
    neo4j
```
Similar but specifying the Neo4J version:

```
docker run --rm -p 7474:7474 -p 7687:7687 -v $(pwd)/data:/data --env NEO4J_AUTH=neo4j/12345 --name neo4j neo4j:3.5.3
```

