# MongoDB

### What is MongoDB

* MongoDB is a document-oriented NoSQL database management system.
* It is one of the most popular databases due to its flexibility, scalability, and ease of use

### What are NoSQL databases

* NoSQL databases is a type of database management
* it is different to SQL in these ways:
  * SQL databases organised into tables with fixed structure
  * NoSQL databases are more flexible and do not have a fixed structure
  * NoSQL DB can store and retrieve data in a more natural way, making it better for applications with complex data structures
  * NoSQL DB is scalable, large amounts of data and traffic is easier to handle as opposed to SQL DB
  * SQL DB however is useful where data is more structured

### Why is MongoDB popular? History?

* It is one of the most popular databases due to its flexibility, scalability, and ease of use
* MongoDB was first released in 2009 by the software company 10gen (now called MongoDB, Inc.).
* It is open source software
* Another reason it is popular is due to it offering flexible data model, automatic sharding, and high availability.
  * Sharding is a way to horizontally scale a DB dividing it into smaller pieces called **shards**. 
  * Data is more manageable after sharding
  * JSON-like document format to store data, which allows for flexible data modeling.

### Make a diagram to show MongoDB architecture

![image](https://user-images.githubusercontent.com/129314018/233045350-1b936922-e4b2-48a8-8b2b-39d93e4c24ba.png)


### Seeding

* Seeding in MongoDB is the process of populating a database with initial data
* DBs in MongoDB may need to be seeded to make sure there is data present for either testing or for the intial stages of the appication where this inital data is needed

### MongoDB Ports

* MongoDB uses port `27017` by default, `27018`, `27019` are alt ports also used for client connections
* `28017` is the default port used by the MongoDB HTTP interface (gives us a web-based interfact to query and admin the database)
* `22` - SSH connections - Linux server
* `443` Used for HTTPs connections to MongoDB which are hosted on a webserver.


### To connect to a MongoDB DB:

 * Install MongoDB client (can also use MongoDB Atlas (cloud based))
 * Start MongoDB service - use `mongod` command
 * Open terminal and type `mongo` to connect to server
 * This starts MongoDB shell
 * In this shell type `use <db-name` and type your specific database name you want to connect to
 * If the data base needs authentication credentials we use the following command
   * `db.auth("<username>", "<password>")`
   * Making sure to replace both `username` and `password` with the corresponding details you have
 * Once you connect succesfully, you can interact with it using the specific mongo shell commands.


