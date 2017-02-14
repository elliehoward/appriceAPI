# appriceAPI
Documentation for the API used in apprice.

The base address of the API is http://appriceapi.herokuapp.com. There are several endpoints at that address, each one with a unique path that will be further explained below.

The layout is as follows:
### Description of what the endpoint does
`the path to be added to the base address` \[VERB\] \(e.g., GET, POST, PATCH, DELETE\)  

`What the request body, or query string looks like` \(if one is needed.\)  

`and lastly a sample response.`

###Add products to users’ saved list:
/api/lists_products \[POST\]  

Sample Request body requires {}


###Create a saved list:
/api/lists \[POST\]  

Sample Request body requires {}


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
Sample Request body requires {t
    agName: ‘customTagName’, productId: clickedOnProductIdAsAnInteger}
Example {tagName: ‘bread’, productId: 12}

###Find a product by type tag(e.g., butter):
/api/type_tags/search \[GET\]  

Query string requires

###Create a new user:
/api/users/register \[POST\]  

Sample Request body requires {}


###Log a user in and create a session:
/api/users/login \[POST\]  

Sample Request body requires {}


###Edit a user’s information(e.g., name, email, password):
/api/users \[PATCH\]  

Sample Request body requires:
{
    email: “users email address”, password: “users password”, fieldtobechanged: “new field’s value”}

Example: {email: “user@gmail.com”, password: “password123”, newpassword: “security”}

###Delete a user:
/api/users \[DELETE\]  

Sample Request body requires {}


###Get an optimized grocery list:
/api/appriceme \[POST\]  

Sample Request body
`{
    "products": [
    {"products":
    {"id": 6, "upc": "015141503495", "plu": null, "name": "Eggland's Best Grade A, White, Large Eggs (dozen)", "brand_name": "Eggsland Best", "brand_type": "Grade A, White, Large", "size": "dozen", "product_image_url": "http://scene7.targetimg1.com/is/image/Target/14711485?wid=1000&hei=1000"}},
    {"products": { "id": 15, "upc": "492840220616", "plu": null, "name": "Horizon Organic 1% Lowfat Milk (Gallon)", "brand_name": "Horizon Organic", "brand_type": "1% Lowfat Milk", "size": "Gallon", "product_image_url": "http://scene7.targetimg1.com/is/image/Target/14937615?wid=1000&hei=1000"}},
    {"products": { "id": 84, "upc": "492310012048", "plu": null, "name": "Post Fruity Pebbles (11 oz.)", "brand_name": "Post", "brand_type": "Fruity Pebbles (11 oz.)", "size": "11 oz.", "product_image_url": "http://target.scene7.com/is/image/Target/14775577?wid=450&hei=450&fmt=pjpeg"}},
    {"products": { "id": 91, "upc": "073435093305", "plu": null, "name": "King's Hawaiian Sweet Sliced Bread (16 oz.)", "brand_name": "King's Hawaiian", "brand_type": "Sweet Sliced Bread (16 oz.)", "size": "16 oz.", "product_image_url": "http://target.scene7.com/is/image/Target/16229584?wid=450&hei=450&fmt=pjpeg"}} ],
    "filteredStores":
    {"data": [
    {"id":1, "name":"Whole Foods Market", "address":"399 4th St, San Francisco, CA 94107", "phone_number":"(415) 618-0066", "store_url": "http://www.wholefoodsmarket.com/stores/soma", "store_image_url": "http://www.trbimg.com/img-568288cb/turbine/ct-whole-foods-overcharging-nyc-customers-20151229", "latitude":"37.780875000000", "longitude":"-122.399641000000", "created_at": "2016-11-14T20:26:16.000Z", "updated_at": "2016-11-14T20:26:16.000Z"},
    {"id":2,"name":"Bristol Farms","address":"Westfield San Francisco Centre, 845 Market St #10, San Francisco, CA 94103","phone_number":"(415) 979-0106","store_url":"http://www.bristolfarms.com/locations/?loc=76","store_image_url":"http://comediva.com/images/stories/bristol2222012.jpg","latitude":"37.784100000000", "longitude":"-122.406144990000", "created_at": "2016-11-14T20:26:16.000Z", "updated_at": "2016-11-14T20:26:16.000Z"},
    {"id":3, "name":"Target", "address": "Metreon, 789 Mission St, San Francisco, CA 94103", "phone_number": "(415) 343-6272"         , "store_url": "http://www.target.com/sl/san-francisco-central/2766#?afid=storeloc&cpng=CA&Inm=san-francisco-central_2766", "store_image_url": "http://www.savingadvice.com/articles/wp-content/uploads/2015/09/237014_Martinsburg_VA_Target_38a77055-e931-4f2c-8455-bf8c7c8925f4-prv.jpg"         , "latitude": "37.784736000000", "longitude": "-122.403691000000" ,"created_at": "2016-11-14T20:26:16.000Z", "updated_at": "2016-11-14T20:26:16.000Z"},
    {"id": 4, "name": "Safeway", "address": "298 King St, San Francisco, CA 94107" ,"phone_number": "(415) 633-1001", "store_url": "http://local.safeway.com/ca/san-francisco-2606.html?utm_source=G&utm_medium=Maps&utm_campaign=G+Places", "store_image_url": "http://www.operating-hours.com/wp-content/uploads/2015/08/SAFEWAY-STORE.jpg", "latitude": "37.776667000000", "longitude": "-122.394109000000" ,"created_at":"2016-11-14T20:26:16.000Z", "updated_at": "2016-11-14T20:26:16.000Z"},
    ]}
    "numOfStores": 3,
    }`

    Sample Response:

    ###Convert optimized list into a more organized format:
    /api/appriceme/convert \[POST\]  

    Req.body requires {}
