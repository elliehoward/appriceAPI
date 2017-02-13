# appriceAPI
Documentation for the API used in apprice.


###Get an optimized grocery list:
/appriceme [POST]
Req.body requires {}

###Convert optimized list into a more organized format:
/appriceme/convert [POST]
Req.body requires {}

###Add products to users’ saved list:
/lists_products [POST]
Req.body requires {}

###Create a saved list:
/lists [POST]
Req.body requires {}

###See all products information:
/products [GET]

###Find product by search term(e.g., ):
/products/search [GET]
Query string requires

###Get the most popular products:
/products/popular [GET]

###Get all the products with info about which stores they’re available at and for what price:
/stores_products [GET]

###Get information about every store:
/stores [GET]

###Get stores filtered by radius
/stores/search [GET]
Example: http://appriceapi.herokuapp.com/api/stores/search?lat=your-latitude-here&long=your-longitude-here&radius=your-search-radius-here



###Get a store by it’s Id:
/stores/:id [GET]
Example: /stores/3 gives you info about a store with the Id 3.

###See all type tags:
/type_tags [GET]

###Associate a product to a type tag(e.g., bread):
/type_tags [POST]
https://appriceapi.herokuapp.com/api/type_tags/
Req.body requires {tagName: ‘customTagName’, productId: clickedOnProductIdAsAnInteger}
Example {tagName: ‘bread’, productId: 12}

###Find a product by type tag(e.g., butter):
/type_tags/search [GET]
Query string requires

###Create a new user:
/users/register [POST]
Req.body requires {}

###Log a user in and create a session:
/users/login [POST]
Req.body requires {}

###Edit a user’s information(e.g., name, email, password):
/users [PATCH]
Req.body requires:
{email: “users email address”, password: “users password”, fieldtobechanged: “new field’s value”}

Example: {email: “user@gmail.com”, password: “password123”, newpassword: “security”}

###Delete a user:
/users [DELETE]
Req.body requires {}
