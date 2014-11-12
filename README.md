# Neo4j Community Docker Image

A nice, clean image of Neo4j Community with appropriate documentation. This image of Neo4j also allows users to mount their Neo4j ``data`` directory via:

# Try It Out

You can read my tutorial blog post or skip to the concise summary below.

## Run (as a test)

- On the server that docker is installed: 
``docker pull seenickcode/neo4j-community``
- Then run your image!  Warning, this will expose the Neo4j brower to the outside word, it's just a test:
``docker run -d --name neo4j --privileged -p 7474:7474 -p 1337:1337 -v /home/core:/var/lib/neo4j/data seenickcode/neo4j-community``
- Then navigate over to ``<yourIP/hostname>:7474`` to ensure your data browser works
- Create a node to test
- Ensure that the ``graph.db`` directory you mounted gets created (located in the directory you ran the ``docker run`` command from).  

## Run (in production)

Obviously in production you're going to want to not allow users to access :7474 (Neo4j browser) or access :1337 (Neo4j shell) so we can change the ``-p`` flag to ensure the ports are only exposed locally to the server.

``docker run -d --name neo4j --privileged -p 127.0.0.1:7474:7474 -p 127.0.0.1:1337:1337 -v /home/core:/var/lib/neo4j/data seenickcode/neo4j-community``
