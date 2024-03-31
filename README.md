# MongoDB Guide 🍃 

- [x] MongoDB is a popular NoSQL database that provides a flexible and scalable solution for storing and managing data. 
- [x] This guide provides information on running MongoDB <img height=20px src="https://skillicons.dev/icons?i=mongo">  both locally and in production environments.
<br>

## Local Running <img align="center" height=60px src="https://github.com/shanibider/MongoDB-Guide/assets/72359805/18adc82d-8062-40ba-8319-af25ca832451">

### Setting Up <img align="center" height=70px src="https://github.com/shanibider/MongoDB-Guide/assets/72359805/563e1e7e-d2bc-4b99-8596-6cfd91466890"> Locally 🏠

To run MongoDB locally on your machine, follow these steps:

1. **Install MongoDB**: Download and install MongoDB from the official website: [MongoDB Download Center](https://www.mongodb.com/try/download/community).

2. **Start MongoDB Server**: Run the `mongod` command in your terminal to start the MongoDB server. This command starts the MongoDB daemon process.

3. **Connect to MongoDB**: Use the MongoDB shell or a client application to connect to the local MongoDB server. The default connection URI is `mongodb://localhost:27017`.

### MongoDB Syntax in Code 🖥️

When connecting to MongoDB locally in your Node.js application, you can use the following syntax:

```javascript
import mongoose from 'mongoose';

// Connect to MongoDB locally
mongoose.connect("mongodb://localhost:27017/<databaseName>", {useNewUrlParser: true});
```

For example, `mongodb://localhost:27017/todolistDB` specifies the connection URI for the local MongoDB instance, where `todolistDB` is the name of the database.

<br>

---

<br>

## Production Running <img align="center" height=60px src="https://github.com/shanibider/MongoDB-Guide/assets/72359805/18adc82d-8062-40ba-8319-af25ca832451">

### MongoDB Atlas 🌐

MongoDB Atlas is a fully managed cloud database service provided by MongoDB. It offers automatic scaling, backup, and high availability, making it ideal for production environments.

### Setting Up <img align="center" height=70px src="https://github.com/shanibider/MongoDB-Guide/assets/72359805/563e1e7e-d2bc-4b99-8596-6cfd91466890"> Atlas ☁️

To run MongoDB in production using MongoDB Atlas, follow these steps:

1. **Sign Up for MongoDB Atlas**: Create an account on the [MongoDB Atlas website](https://www.mongodb.com/cloud/atlas) if you haven't already.

2. **Create a Cluster**: Create a new cluster in MongoDB Atlas. A cluster is a group of MongoDB servers that store your data.

3. **Get Connection URI**: MongoDB Atlas provides a connection URI that you can use to connect to your cluster from your application. This URI includes authentication credentials and other connection options.

### MongoDB Syntax in Code 🖥️

When connecting to MongoDB Atlas in your Node.js application, you can use the following syntax:

```javascript
import mongoose from 'mongoose';

// Connect to MongoDB Atlas
mongoose.connect(process.env.MONGODB_URI);

// MONGODB_URI (in .env file)
MONGODB_URI = "mongodb+srv://<username>:<password>@<clusterName>.mongodb.net/?retryWrites=true&w=majority";
```

Here, `process.env.MONGODB_URI` refers to an environment variable that contains the connection URI for your MongoDB Atlas cluster.


###### MongoDB Cloud 
<img align="center" src="https://github.com/shanibider/MongoDB-Guide/assets/72359805/b3fc91f8-7df8-4166-94ad-5b79d56316ac">

<br>

---

<br>

## Using Models 🛢

In production applications, defining `models` is crucial for maintaining data consistency and structure.
**here's a general syntax for defining models in MongoDB using Mongoose in a Node.js application:**

```javascript
const mongoose = require('mongoose');

// Define schema for the model
const schemaName = new mongoose.Schema({
  // Define fields and their types
  fieldName1: { type: FieldType, required: true },
  fieldName2: { type: FieldType, default: DefaultValue },
  fieldName3: { type: FieldType },
  // Add more fields as needed
});

// Create model from schema
const ModelName = mongoose.model('ModelName', schemaName);

module.exports = ModelName;
```

### Explanation 🔦:

1. **Import Mongoose**: Import the Mongoose library into your Node.js application.

2. **Define Schema**: Use `mongoose.Schema()` to define the schema for your model. The schema defines the structure of documents in the collection, including the fields and their types.

3. **Define Fields**: Inside the schema definition, specify the fields of the document along with their types. You can also specify additional options like `required` and `default`.

4. **Create Model**: Use `mongoose.model()` to create a model from the schema. The model represents a collection in the MongoDB database and provides an interface for interacting with the documents.

5. **Export Model**: Export the model so that it can be used in other parts of your application.



**🔎Here's an example of defining a model for an e-commerce order in a Node.js application:**:
```javascript
import mongoose from 'mongoose';

// Define schema for order
const orderSchema = new mongoose.Schema({
  orderItems: [{ type: mongoose.Schema.Types.ObjectId, ref: 'Product' }],
  shippingAddress: { type: String, required: true },
  // Add more fields as needed
});

// Create model from schema
const Order = mongoose.model('Order', orderSchema);
```

With the `Order` model defined, you can easily interact with order data in your MongoDB Atlas database. <br>

###### MongoDB Cloud Collection
<img align="center" src="https://github.com/shanibider/MongoDB-Guide/assets/72359805/283865f8-4e74-42de-8db7-908372a58f14">


<br>

---

## Conclusion
MongoDB is a versatile database solution that can be run both locally and in production environments.
Whether you're developing a new application or scaling an existing one, MongoDB offers the flexibility and features needed to meet your data storage needs.
<br>



<div align="center">
<img  height=450px src="https://github.com/shanibider/MongoDB-Guide/assets/72359805/d0d21cdc-dccd-4988-86db-4ab82281025f">
</div>

## 📫 Connect with me 😊
[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/shani-bider/)
[![portfolio](https://img.shields.io/badge/my_portfolio-000?style=for-the-badge&logo=ko-fi&logoColor=white)](https://shanibider.github.io/Portfolio/)
[![gmail](https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:shanibider@gmail.com)

<footer>
<p style="float:left; width: 20%;">
Copyright © Shani Bider
</p>
</footer>

## License📄

This project is licensed under the MIT License.
