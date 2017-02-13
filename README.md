# appriceAPI
Documentation for the API used in apprice.

The base address of the API is http://appriceapi.herokuapp.com. There are several endpoints at that address, each one with a unique path that will be further explained below.

The layout is as follows:
### Description of what the endpoint does
`the path to be added to the base address` \[VERB\] \(e.g., GET, POST, PATCH, DELETE\)
`What the request body looks like` \(if one is needed.\)  

`and lastly a sample response.`

###Get an optimized grocery list:
/api/appriceme \[POST\]
Req.body requires {}

###Convert optimized list into a more organized format:
/api/appriceme/convert \[POST\]
Req.body requires {}

###Add products to users’ saved list:
/api/lists_products \[POST\]
Req.body requires {}

###Create a saved list:
/api/lists \[POST\]
Req.body requires {}

###See all products information:
/api/products \[GET\]

###Find product by search term(e.g., ):
/api/products/search \[GET\]
Query string requires

###Get the most popular products:
/api/products/popular \[GET\]

###Get all the products with info about which stores they’re available at and for what price:
/api/stores_products \[GET\]

###Get information about every store:
/api/stores \[GET\]

###Get stores filtered by radius
/api/stores/search \[GET\]
Example: http://appriceapi.herokuapp.com/api/stores/search?lat=your-latitude-here&long=your-longitude-here&radius=your-search-radius-here



###Get a store by it’s Id:
/api/stores/:id \[GET\]
Example: /stores/3 gives you info about a store with the Id 3.

###See all type tags:
/api/type_tags \[GET\]

###Associate a product to a type tag(e.g., bread):
/api/type_tags \[POST\]
https://appriceapi.herokuapp.com/api/type_tags/
Req.body requires {tagName: ‘customTagName’, productId: clickedOnProductIdAsAnInteger}
Example {tagName: ‘bread’, productId: 12}

###Find a product by type tag(e.g., butter):
/api/type_tags/search \[GET\]
Query string requires

###Create a new user:
/api/users/register \[POST\]
Req.body requires {}

###Log a user in and create a session:
/api/users/login \[POST\]
Req.body requires {}

###Edit a user’s information(e.g., name, email, password):
/api/users \[PATCH\]
Req.body requires:
{email: “users email address”, password: “users password”, fieldtobechanged: “new field’s value”}

Example: {email: “user@gmail.com”, password: “password123”, newpassword: “security”}

###Delete a user:
/api/users \[DELETE\]
Req.body requires {}
