```js
//connect to mongodb
//create one method to create a connection to the database, and another method to return this connection when it's successful
//import this into the main app.js file to connect to the database
const { MongoClient } = require('mongodb');

let;
let dbConnection;

module.exports = {
    connectToDb: (callbackFunction) => {
        MongoClient.connect(dbConnectionString)
            .then((client) => {
                dbConnection = client.db();
                return callbackFunction();
            })
            .catch((err) => {
                console.log('unable to connect to db\n' + err);
                return callbackFunction(err);
            })
    },
    getDb: () => {
        return dbConnection;
    }
}
```