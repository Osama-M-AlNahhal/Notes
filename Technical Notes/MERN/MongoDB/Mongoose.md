*ODM Library (Object-Document Mapping)*


![[Mongoose.png]]

# How it works
*inside our models folder*

1. create a .js file in the models folder and name it appropriately 
2. setup mongoose inside the file
```js
const mongoose = require('mongoose');
const Schema = mongoose.Schema;
```

3. create a schema for the collection :
   - a schema shows what values and properties that are required for any document (model) that's based on that schema. 
```js
const flavorSchema = new Schema({
    field: {
        type: String,
        require: true
    },
    field2: {
        type: String,
        require: false
    }
}, { timestamps: true });
```

4. create a model based on the schema
   - it's important to name the model as the singular of the collection's name, because mongoose with look for the collection with the plural name of our model
```js
const flavor = mongoose.model('flavor', flavorSchema);
```

5. export the model, import it in the index.js file and use it.
```js
module.exports = modelName
```

---

