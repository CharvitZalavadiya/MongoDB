# MongoDB Documentation
### 01 : Introducation
- Database - Collection of data in a structured way
- SQL - Structured Query Language
- RDBMS - Relational Database Management System
- NoSQL alias Non SQL alias Non Relational
- In simple terms: A NoSQL database is a Key-Value Database
- A NoSQL database provides : 
  - A mechanism for storage and retrieval of data
  - The data is NOT modeled in relational or tabular format
  - Extremely useful, powerful and high performance database in large big data applications, large distributed network architecture apps etc
  - A large variations and flavors of NoSQL are available in market - MongoDB, Amazon DocumentDB, Google Datastore, Amazon DynamoDB etc
- Let's try and understand in simple terms:
  - MongoDB is a Free and Open Source Cross Platform Document-Oriented Database
  - MongoDB is classified as NoSQL Database Program
  - MongoDB uses JSON-like document with schemas

- A document-oriented database provides APIs or a query/update language that exposes the ability to query or update based on the internal structure in the document
- But what the hell is a document?
  - MongoDB documents are composed of field-and-value pairs and have the following structure
    { field1: value1, field2: value2 }

- Let's understand what MongoDB is NOT:
  - MongoDB is NOT a RDBMS system
  - MongoDB does not have any concept of joins!
  - MongoDB is NOT tough or complicated




###02 : Installation
- There are 3 ways to install and use MongoDB
  - Community Server
  - Visual Studio Extension
  - MongoDB Atlas

- Let's install MongoDB on our machines via Community Server
  - Visit official website: http://mongodb.com
  - Download the latest stable version from Community Server
  - The community server will also install the following apps
	- Community Server
	- Compass - GUI Tool for MongoDB

- MongoDB - Visual Studio Extension
  - Search and Install MongoDB Visual Studio Code - Extension

- MongoDB - Atlas ( via Cloud MongoDB )
  - Cloud-Hosted and Fully Managed MongoDB
  - Pay as you go model
  - Very cost-effective
  - Fully secured and reliable



###03 : Databases, Documents and Collections
- Database : Database is a collection of data
- In MongoDB context :
  - Database can also be described as a physical container for collections
  - A Database can have any number of collections
  - Each database gets it's own set of files on the file system
  - A MongoDB server can hosts multiple databases inside it

- Collections :
  - Collection is a group of MongoDB Documents
  - Unlike tables, Collections does not have any schema definition
  - Unlike RDBMS Database - the collections DO NOT have any concept of JOINS
  - However we can achieve joins functionality using Aggregations in MongoDB

- Documents :
  - Document in MongoDB is a set of "key-value" Pairs
  - Every document in MongoDB has a unique value via Key "_id"
  - Documents have flexible and dynamic schema
  - Document schema is user-defined and is not Fixed or Static
  - Documents can hold any data as along as they are valid data types in MongoDB
  - Documents within a collection can have different schema or fields
  - Documents within a collection are related data belonging to a particular subject



###04 : MongoDB Compass App
- Documents -> Collection -› Database



###05 : VS Code Extension
- Go to Extension in VS Code in search for MongoDB for VS Code and install it.
- To start work with terminal in vs code enter ctrl+p and write ">" then select Launch Mongo Shell this will open MongoDB Shell inside that do CRUD operations. and exit that shell press ctrl+c two times.



###06 : Create and Drop Databases
- Creating and Dropping Databases
  - Creating Databases
	- use <database-name>
	- The newly created database will NOT visible unless we insert any document inside it
	- Make sure we see the message "switched to db <database-name>"
  - Check your working space DB by hitting the command "db"
  - To remove Database use the command - db.dropDatabase()



###07 : Create and Drop Collections
- Creating Collections
  - db.createCollection(name, options)
- Dropping Collections
  - db.collection.drop()



###08 : Data Types in MongoDB
- BSON
- JSON
- Integer
- Boolean
- Double
- Arrays
- Object
- Null
- Date
- Timestamp
- Object Id
- Code

- Difference between BSON and JSON
  - JSON based databases usually return query results which can be effortlessly parsed, having modest or nix transformation, straightforwardly by the use of JavaScript along with most well-liked programming languages.
  - In the case of MongoDB, data representation is done in JSON document format, but here the JSON is binary-encoded, which is termed as BSON.
  - BSON is the extended version of the JSON model, which is providing additional data types, makes performance to be competent to encode and
decode in diverse languages and ordered fields.

- Binary encoded json = BSON, it have some extended datatypes which are not supported in JSON like, date, timestamp, Object Id etc.



###09 : Insert Documents in Collections
- To Insert any document into Collection
  - Db.<collection-name>.insert({ "name": "Arc Tutorials"})
- To insert many documents at once into collection
  - Db.<collection-name>.insertMany({ "name": "Arc Tutorials"}, { "name": "Sai Ram"})

- Every document that we insert will have a unique key "_id"
  - the value for this key is always unique and 24 character
  - _id as a Primary Key in your collection
- Can we change the value of _id??
  - Yes, we can change it but it is tricky
  - Recomanded : DO NOT DO THIS - changing the _id value



###10 : Update Documents in MongoDB
- Update can be applied with
  - update
  - updateOne
  - updateMany

- Db. <collection-name>.update(\
	{ "name": "Arc Tutorials"},\
	$set: {\
		"key": "value"\
	}\
  )



###11 : Read Documents From Collection in MongoDB
- find() - finds all documents in collection
  - db.collection.find()
- findOne() - find first document in collection
- find ({"key1":"value1", "key2": "value2"}) - by setting query conditions
- findOneAndReplace({"key1":"value", "key2": "value2"}, < replacement>)
- findOneAndDelete({"key1":"value", "key2": "value2"})

- To know all the find methods we can perform enter the command "db.collection.find" this will show you all the ways in which you can perform find.



###12 : Delete Documents From Collection in MongoDB
- deleteOne() - finds all documents in collection
  - db.collection.find()
  - Example: db.orders.deleteOne({"_id" : Objectld("563237a41a4d68582c2509da") } );
- deleteMany({})
  - Will delete many documents at once
  - When passed with empty curly brace - it will delete all documents in collections
  - Example: db.orders.deleteMany({});



###13 : Queries in MongoDB
- We can use multiple operations inside the Find method
- Using operations we add more search power to Find method
- Various conditions that can be used are:
  - Equality (Eq)
  - Less Than (lt)
  - Less than equal (lte)
  - Greater Than (gt)
  - Greater Than Equal (gte)
  - Not Equal

- All conditions "MUST" be satisfied in order to return the document
  - $and - And operation
	- Match all conditions mentioned in the Find method
	- E.g db.leads.find ({ $and: [{}, {} ]})
  - $or - OR operation
	- Match any condition in the find method

- Find method with tax less than 30 --> db. leads. find({"Tax": { $lte: "30" }})

- Find method with tax grater than equal 30 --> db. leads. find({"Tax": { $gte: "30" }})

- And operator with Find method --> db. leads.find({$and : [{"Tax": "30" }, {"Salary": {$lte: "120000" }} ]});

- OR operator with Find method --> db. leads.find({$or : [{"Tax": "30" }, {"Salary": {$lte: "100000"}} ]});



###14 : Find Specific Fields in MongoDB
- db.leads.find({}, {"city": 1, "_id": 0 })
  - here all the documents that have "city" as a key they will show the city and id will not be shown as it have given 0

- In this method you can only show or hide fields with 1 and 0 but you can not use it togather like some field have 1 to show and some have 0 to not show either you can get the properties with 1 or you can get proprties for 0.


###15 : Projection in MongoDB
- find is basically projection in mongodb it is uses like you have 100 keys in one document and you need only few of them and all others are not needed then you can do this.



###16 : Aggregation in MongoDB
- What is Aggregation in MongoDB?
  - Aggregate is very similar to the find command, where you can provide the criteria for your query in the form of JSON documents
  - The key element in aggregation is called the pipeline
  - It also helps us in performing few operations like min, max, sum etc
  - The command to use Aggregation is :
	- db.leads.aggregate(pipeline, options)
	- What's pipeline?
	  - A sequence of data aggregation operations or stages
	  - Pipeline is an Array
	- What are options?
	  - Documents can be passed as well

- What are valid Aggregate Stages?
  - $count
  - $group
  - $limit
  - $lookup
  - $match
  - $merge
  - $sort
  - $project
  - $unwind
  - $unset
  - And many more

- Example :
var pipeline = [\
	{$group : ("_id": "city"}},\
	{ $sort: {"leadName": 1} },\
	{ $limit: 3 }\
];\
db. leads. aggregate(pipeline);



###17 : Limit and Skip in MongoDB
- We may not always want all documents all the time
  - db.collection.find().limit(4);
- We may want to skip some documents we don't need
  - db.collection.find().skip(3);
- Always remember - skip will skip sequentially not random or advaoc



###18 : Sorting in MongoDB
- We will need to sort the record set before passing it to next logical operation
- To sort we can use the below command
  - db.collection.find().sort({"leadName": 1 })
  - 1: means ascending
  - -1 : means descending



###19 : Creating Indexes in MongoDB
- Indexes are the fastest way to find information
- Indexes concept is same as that you already would know in SQL
- By default - every collection will have an Index on "_id" key
- How do we create a index on collection?
  - db.leads.ensurelndex("leadName": 1)



###20 : Back Up and Recover Data
- Steps to create Back up of MongoDB Data
  - Step 1 - First create a folder where you want to save your data
  - Step 2 - Next, Runt the command "mongodump.exe"
  - Step 3 - Verify the data dump and folder dumped correctly



###21 : Interview Questions
1. What is MongoDB?
	- MongoDB is a NoSQL document-oriented database that stores data in JSON-like
documents with dynamic schemas.
	- It is designed to handle large volumes of unstructured data.

2. What is a document in MongoDB?
	- A document is a set of key-value pairs stored in a BSON format in MongoDB. BSON is a binary representation of JSON.

3. What is a collection in MongoDB?
	- A collection in MongoDB is a group of documents that share a similar structure. It is equivalent to a table in a relational database.

4. What is a replica set in MongoDB?
	- A replica set in MongoDB is a group of MongoDB servers that store the same data to provide redundancy and high availability.

5. What is sharding in MongoDB?
	- Sharding in MongoDB is a method of partitioning data across multiple servers to improve performance and scalability.

6. What is indexing in MongoDB?
	- Indexing in MongoDB is the process of creating an index on a field in a collection to improve query performance.

7. What are the different types of indexing in MongoDB?
	- MongoDB supports several types of indexing, including single field, compound, multi-key, text, and geospatial indexing.

8. What is MapReduce in MongoDB?
	- MapReduce is a data processing technique in MongoDB that involves mapping data to a set of key-value pairs, reducing the values based on the keys, and aggregating the results.

9. What is the aggregation pipeline in MongoDB?
	- The aggregation pipeline is a framework in MongoDB that allows for the processing of data through a series of stages, including filtering, sorting, grouping, and transforming data

10. What is the difference between update and save in MongoDB?
	- The update method in MongoDB modifies existing documents, while the save method either updates an existing document or inserts a new document if one does not already exist.

11. What is GridFS in MongoDB?
	- GridFS is a specification for storing and retrieving large files, such as images and videos, in MongoDB.

12. What is the difference between a primary key and a secondary key in MongoDB?
	- A primary key in MongoDB is a unique identifier for a document, while a secondary key is used for indexing and querying data.

13. How does MongoDB ensure data consistency?
	- MongoDB uses a two-phase commit protocol to ensure data consistency in distributed environments.

14. How does MongoDB handle schema changes?
	- MongoDB allows for flexible schemas, and schema changes can be made without affecting existing data.

15. How does MongoDB handle transactions?
	- MongoDB supports multi-document transactions that allow for atomicity, consistency, isolation, and durability (ACID) properties.

16. What is the role of the mongod process in MongoDB?
	- The mongod process is the primary daemon process in MongoDB that manages data storage, indexing, and access.

17. What is the role of the mongo shell in MongoDB?
	- The mongo shell is a command-line interface that allows users to interact with MongoDB and perform administrative tasks.

18. How does MongoDB handle security?
	- MongoDB provides several security features, including authentication, authorization, encryption, and auditing.

19. What is the difference between a join and a lookup in MongoDB?
	- A join in MongoDB involves combining data from multiple collections, while a lookup involves retrieving related data from another collection.

20. How does MongoDB handle data backup and recovery?
	- MongoDB provides several backup and recovery options, including hot backups, point-in-time recovery, and incremental backups.

21. Difference Between Update and FindOneAndUpdate?
	- update(): Is meant to perform an atomic update operation against "one or more" documents matched by it's query condition in a collection. It returns the number of modified documents in it's response.
	- findOneAndUpdate(): Has the purpose of both processing an update statement on a "singular" document, as well as retrieving the content of that "singular" document. The state returned depends on the value of the "new" option as passed to the operation. Where true the "modified" document is returned. Where false the "original" document is returned before any modification. The latter form is the default option.

22. Difference Between drop and remove?
	- The drop() function Removes the specified collection from the database.
	- The remove() function Deletes documents from a collection.

23. Difference Between createlndex and relndex?
	- The createlndex() function Builds an index on a collection.
	- The relndex() function Rebuilds all existing indexes on a collection.

24. How to get system info on which MongoDB is running?
	- We can get system info on which MongoDB is running using : hostinfo
	- db.hostInfo() method Returns a document with information about the system MongoDB runs on

25. How to remove the current database?
	- db.dropDatabase() method Removes the current database.

26. How to rename a collection?
	- db.collection.renameCollection() method Changes the name of a collection.

27. What is the difference between findModify() and findOneAndUpdate()
	- db.collection.findAndModify() method Atomically modifies and returns a single document.
	- db.collection.findOneAndUpdate() method Finds a single document and updates it.
	- The difference is in the "automatic" process