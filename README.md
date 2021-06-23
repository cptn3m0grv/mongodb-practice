# MongoDB

* MongoDB is a document database designed for ease of development and scaling.
* It is intuitive and easy to use NoSQL database.
* Available as community and enterprise edition.
* The community edition itself is very powerful

## Mongo vs MongoD

1. Mongo -> It is the command-line shell that connects to a specific instance of MongoD.
2. MongoD -> It is "Mongo Daemon" it's basically the host process for the database.

## Terminologies

SQL Terminologies ---> MongoDB Terminologies
Database ---> Database
Table ---> Collections (JS Objects)
Rows ---> Documents (BSON)
Columns ---> Fields

* BSON is more efficient than JSON
Example: 
```
{
    name: "sue",
    age: 26,
    status: "A",
    groups: ["news", "sports"]
}
This is knows as "field:value" pair
```

## Installation
Download MongoDB community server for respective OS, from internet
```
mongodb.com/try/download/community 
```
* Install it as a service, don't forget to add it in environment variables

* MongoDB Compass -> It is basically a GUI version of the database
* Capped Collection will keep deleting older data 


## Usage

### Databases

#### View All Databases
```
show dbs;
```

#### Creating or switch a databse
```
use <database_name>
```

#### Verify the database name
```
db;
```

#### Delete/Drop Database
```
show dbs;
use <db_name>;
db;
db.dropDatabase();
```

### Collections

#### To View Collections
```
show collections;
```

#### Create a new Collection
```
db.createCollection('name');
```

#### Delete a Collection
```
db.<collection name>.drop();
```

### Documents/Rows

#### Insert a row in collection
```
db.<collection_name>.insert({
    'name': 'gaurav',
    'age': 20,
    'skills': ["mongo", "express", "react", "node"]
})
```

#### Insert multiple rows in a collection
```
db.<collection_name>.insertMany([
    {
        "name": "gaurav",
        "age": 21,
        "skills": ["python", "flask"]
    },
    {
        "name": "gaurav",
        "age": 21,
        "skills": ["devops", "cloud"]
    }
]);


ObjectId will be returned, acts like primary key
```

#### Show rows in a collection
```
db.<collection_name>.find();
            or
        we can also prettify it
db.<collection_name>.find().pretty();
```

### Search

#### Search for a particular details
```
db.<collection_name>.find({"age": 20})
```

#### Limit the outputs to be displayed
```
db.<collection_name>.find({"age": 20}).limit(3);

Will only display 3 results at max
```

#### Count the number of rows in the output
```
db.<collection_name>.find().count();
```

#### Sorting ascending/descending
```
db.<collection_name>.find().sort({age:1}).prety(); //sorting in ascending order
db.<collection_name>.find().sort({age:-1}).pretty(); //sorting in descending order
```

#### Find one row
```
db.<collection_name>.findOne({name: "gaurav"}); //will terminate as soon as first instance is found
```

### Updating the database

#### Update a row
```
db.<collection_name>.update({name: "gaurav"}, <New Object>);
```

#### Insert a row, if no matches found
```
db.<collection_name>.update(<search_param>, <New Object>, {upsert: true});
```

#### Delete a row
```
db.<collection_name>.remove(<search_param>);
```

#### Increment operator
```
db.<collection_name>.update(
    <search_param>, 
    {
        $inc:{
            member_since: 2
        }
    }
);
```

#### Rename operator
```
db.<collection_name>.update(
    <search_param>,
    {
        $rename:{
            member_since: "member"
        }
    }
)
```

#### Less than operator/ Greater than/ less than equals/ greater than equals
```
db.<collection_name>.find({member_since: {$lt: 90}});
db.<collection_name>.find({member_since: {$gt: 10}});
db.<collection_name>.find({member_since: {$lte: 90}});
db.<collection_name>.find({member_since: {$gte: 10}});
```

## MongoDB Atlas

* Atlas is basically database on cloud
* It offers multiple features
    * We can also give access to specific user as well
    * The access can also be temporary
* Can be connected via mongoDB Compass or via code as well