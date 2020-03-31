# getting_started

## Team Chat on Matrix
We use Matrix to communicate (https://matrix.org/). Riot is the standard client for Matrix (https://about.riot.im/)

How to get started:
- Download Riot or start the web app: https://about.riot.im/downloads
- Create an account on the free matrix.org homeserver
- send us your username (something like @myusername:matrix.org)


## public graph database
The database is hosted on covid.petesis.com with a public read only user.

Currently there is an issue with Chrome/Chromium and the SSL certificate. You cannot access the Neo4j Browser via HTTPS in Chrome.

- Neo4j browser: https://covid.petesis.com:7473
- Bolt URL: bolt://covid.petesis.com:7687

- user: public
- password: corona



## Adding your own data
This section provides some guidelines on adding data to the project. Feel free to use the CovidGraph Data Sources channel for any further questions.
### 1. Check which data is already in the knowledge graph
- add your dataset to the list here: https://ethercalc.org/3d1whloznieq
- If needed, add if your loading script has a dependency on other data. If you are linking your newly added data to existing nodes, check the sourceguid properties on these nodes to determine the dependencies.
 
### 2. Follow the suggested naming conventions for the nodes and relationships you create.
- See https://neo4j.com/docs/cypher-manual/current/syntax/naming/
- Node labels in camel case with an uppercase first letter (GeneSymbol)
- Relationships in all caps with underscores (HAS_BODY)
- properties in camel case (numberOfInfections)

### 3. Ensure data traceability
- Make sure that each node/relationship you import has these two properties:
- Add a unique sourceguid property to the nodes/relationships you create, so we can trace back where data comes from.
- If possible, add a sourceroutine property that refers to the script/query that imported the data. 

### 4. Think about data modeling
- Check the existing model for the graph. 
- Re-use existing node labels and relationship types if possible. If not possible, document the usecase for your node label and relationship.
- Create indexes/constraints if necessary. This will make the data faster to search, and also ensure quality (e.g. a given property must exist)
- New to graph data modeling? There’s some great material out there on which pitfalls to avoid: https://neo4j.com/blog/data-modeling-pitfalls/

