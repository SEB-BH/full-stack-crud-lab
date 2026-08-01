<h1>
  <span class="headline">MERN Inventory Management Front end</span>
  <span class="subhead">Exercise</span>
</h1>

## Introduction

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