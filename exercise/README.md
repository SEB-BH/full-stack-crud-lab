<h1>
  <span class="headline">Full Stack CRUD Lab</span>
  <span class="subhead">Exercise</span>
</h1>

## Requirements

We are building an app with the following endpoints:

| HTTP Method | Response | Endpoint        | Use Case             |
| ----------- | -------- | --------------- | -------------------- |
| POST        | 201      | `/products`     | Create a product     |
| GET         | 200      | `/products`     | List all products    |
| GET         | 200      | `/products/:id` | Get a single product |
| PUT         | 200      | `/products/:id` | Update a product     |
| DELETE      | 200      | `/products/:id` | Delete a product     |




## Part 2: Create the Product Model

1. Create a models folder
2. In your models folder create a file `Product.js`
3. The client asked for the following things to track about the products:


|  **Field**  | **Data Type** |                               **Validation**                              |
|:-----------:|:-------------:|:-------------------------------------------------------------------------:|
|    Title    |     String    |                               Required, trim                              |
| description |     String    |                               maxLength: 500                              |
|   category  |     String    | required, enum: ["electronics", "food", "clothing", "furniture", "other"] |
|    price    |     Number    |                             required, min: 0.1                            |
|   quantity  |     Number    |                              required, min:0                              |


4. Add `{timestamps:true}` to the Schema
5. Create the model and export it


## Part 3: Create the controller and mount it

1. Create a controller folder and in the folder create a product.controller.js
2. Import the model here and also import the router from express and export it at the bottom of the file. (If you don't remember the exact syntax refer to your project 2)
3. Mount the controller in your app.js on `/products`


## Part 4: Creating the core endpoints

Now that we have created the model and controller file it's time to build our endpoints. Remember to test every single route after creating it in the controllers file

### POST /create

1. Create the POST route for creating a new product here. This endpoint should take in the data for a new Product in the requests body and create a new product in the database if it passes the validation
2. Make sure to send back the status of `201` when the product is created
3. wrap all your routes in `try catch` and send back the error message for now
4. Test your route in postman. Below is a sample body you can use:

```json
{
  "title": "Wireless Keyboard",
  "description": "Bluetooth mechanical keyboard",
  "category": "Electronics",
  "price": 49.99,
  "quantity": 20
}
```


### GET /products

1. Now create the GET route for getting all the products from the database
2. This route should return all the products from the database as `JSON`
3. Test this route on postman


#### GET /products/:id

1. Create the route for 1 product. When a request is sent to `/products/:id` the product with this id should be fetched and returned as a response
2. Test this route on Postman


### PUT /products/:id
1. Create a `PUT` route that recieves a request at `/products/:id` and updates the product with this id based on the request body
2. Test this route in postman


### DELETE /products/:id
1. Create a `DELETE` route that recieves a request at `/products/:id` and deletes the product with this id
2. Test this route in postman



## Bonus: Statistics Endpoints

1. Add 2 more endpoints: `/low-stock` and `/statistics`
2. The `/low-stock` endpoint should return an array of objects of all the items that are `quantity` below 3
3. For the `/statistics` endpoint return something like this:
```json
{
  "totalProducts": 82,
  "totalValue": 54343,
  "lowStockItems": 5
}
```



# MERN Inventory Management Front End

For this lab we will build the front end for the product management backend API from the previous lab.

## Minimum requirements

The client wants the following pages:

| Component              | Route              |
|------------------------|--------------------|
| Homepage.jsx           | /                  |
| AllProductPage.jsx     | /products          |
| ProductDetailsPage.jsx | /products/:id      |
| CreateProductPage.jsx  | /products/create   |
| UpdateProductPage.jsx  | /products/:id/edit |



As well as a Navbar that should be at the top of all these components


## BONUS 1: Add a service file

1. If you haven't already create a `productService.js`. This should be a file that contains service functions that are calling the API with the proper CRUD operations:
```js
getProducts()
getProductById(productId)
createProduct(productData)
updateProduct(productId, productData)
deleteProduct(productId)
```

2. Make sure to use `axios.create()` to make your functions better



## BONUS 2: Add an Error state and Loading state

1. In the components fetching data: `AllProductPage.jsx` and `ProductDetailsPage.jsx` add loading states and error states
2. Use a spinner from antd package if you want to show a spinner for the loading state
3. Make error messages for the POST and PUT calls as well. The state for the error should be set after the user submits the form


## BONUS 3: Statistics routes

1. In the previous lab we created extra endpoints for inventory stastics with `/low-stock` and `/statistics`. Make the pages for these. It can be 1 page or 2 pages
2. If you want you can use a library like [material ui](https://mui.com/) to display the data in a nice way for the client
