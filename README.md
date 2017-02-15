# appriceAPI
Documentation for the API used in apprice.

The base address of the API is http://appriceapi.herokuapp.com. There are several endpoints at that address, each one with a unique path that will be further explained below.

The layout is as follows:
### Description of what the endpoint does
`the path to be added to the base address` \[VERB\] \(e.g., GET, POST, PATCH, DELETE\)  

`Sample request body, or query string.` \(if one is needed.\)  

`and lastly a sample response, if applicable.`

###Create a saved list:
`/api/lists` \[POST\]  

Sample Request body `{userId: 1, name: "Work week"}`  

Sample Response `[{id: 1}]` \(This is the id of the newly created list.\)


###Add products to users’ saved list:
####This is where you send the products to be saved on a list along with the list id that comes back from the above route.
`/api/lists_products` \[POST\]  

Sample Request body `{listId: 1, products: [
    {product Object},
    {product Object},
    {product Object}
    ]
}`


###See all products information:
`/api/products` \[GET\]  


###Find product by search term(e.g., milk, Tostitos):
`/api/products/search` \[GET\]  

Sample Query string
`/api/products/search?name=milk`

###Get the most popular products:
`/api/products/popular` \[GET\]  


###Get all the products with info about which stores they’re available at and for what price:
`/api/stores_products` \[GET\]  


###Get information about every store:
`/api/stores` \[GET\]  


###Get stores filtered by radius
`/api/stores/search` \[GET\]  

Sample Query string  
 `api/stores/search?lat=your-latitude-here&long=your-longitude-here&radius=your-search-radius-here`



###Get a store's information by it’s Id number:
`/api/stores/:id` \[GET\]  


###See all type tags:
`/api/type_tags` \[GET\]  


###Associate a product to a type tag(e.g., bread):
`/api/type_tags` \[POST\]  

Sample Request body
`{tagName: ‘bread’, productId: 12}`

###Find a product by type tag association(e.g., butter):
####This is where you get JSON of products that are associated with the tag in the query string.
`/api/type_tags/search` \[GET\]  

Sample Query string `/api/type_tags/search?name=peanut+butter`

###Create a new user:
`/api/users/register` \[POST\]  

Sample Request body `{"first_name": "user's name", "last_name": "user's lastname", email: blahblah@gmail.com, password: userspass(it will be hashed.)}`


###Log a user in and create a session:
`/api/users/login` \[POST\]  

Sample Request body `{email: “user@gmail.com”, password: “password123”}`


###Edit a user’s information(e.g., name, email, password):
####Whatever field needs to be changed needs to be added in the body as new_fieldname
`/api/users` \[PATCH\]  

Sample Request body:
`{email: “user@gmail.com”, password: “password123”, new_password: “security”}`

###Delete a user:
`/api/users` \[DELETE\]  

Sample Request body `{email: “user@gmail.com”, password: “password123”}`


###Get an optimized grocery list:
####This is where you send the products you want, along with search preferences. The stores should already be filtered from the /stores/search route and the data should be formatted as follows:
`/api/appriceme` \[POST\]

    `{products:
        [
          {product Object},
          {product Object},
          {product Object},
          {product Object}
        ],
      filteredStores: {
            data: [
                {store Object},
                {store Object},
                {store Object}
            ],
        }
      numOfStores: 3
    }`  

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


    Sample Response  

`[ { id: 23,
 store_id: 3,
 product_id: 6,
 availability: true,
 price: 3.99 },
{ id: 66,
 store_id: 3,
 product_id: 15,
 availability: true,
 price: 7.49 },
{ id: 397,
 store_id: 3,
 product_id: 86,
 availability: true,
 price: 2.39 },
{ id: 418,
 store_id: 3,
 product_id: 91,
 availability: true,
 price: 3.19 } ]`

###Convert optimized list into a more organized format:
####This is where you send the response that comes from /api/appriceme
`/api/appriceme/convert` \[POST\]  

Request body Sample
`[ { id: 23,
    store_id: 3,
    product_id: 6,
    availability: true,
    price: 3.99 },
  { id: 66,
    store_id: 3,
    product_id: 15,
    availability: true,
    price: 7.49 },
  { id: 397,
    store_id: 3,
    product_id: 86,
    availability: true,
    price: 2.39 },
  { id: 418,
    store_id: 3,
    product_id: 91,
    availability: true,
    price: 3.19 } ]`

    Sample Response  

    `[{
    "id": 3,
    "name": "Target",
    "address": "Metreon, 789 Mission St, San Francisco, CA 94103",
    "phone_number": "(415) 343-6272",
    "store_url": "http://www.target.com/sl/san-francisco-central/2766#?afid=storeloc&cpng=CA&Inm=san-francisco-central_2766",
    "store_image_url": "http://www.savingadvice.com/articles/wp-content/uploads/2015/09/237014_Martinsburg_VA_Target_38a77055-e931-4f2c-8455-bf8c7c8925f4-prv.jpg",
    "latitude": "37.784736000000",
    "longitude": "-122.403691000000",
    "created_at": "2016-11-14T20:26:16.000Z",
    "updated_at": "2016-11-14T20:26:16.000Z",
    "products": [
      {
        "id": 6,
        "upc": "015141503495",
        "plu": null,
        "name": "Eggland's Best Grade A, White, Large Eggs (dozen)",
        "brand_name": "Eggsland Best",
        "brand_type": "Grade A, White, Large",
        "size": "dozen",
        "product_image_url": "http://scene7.targetimg1.com/is/image/Target/14711485?wid=1000&hei=1000",
        "created_at": "2016-11-14T20:26:16.000Z",
        "updated_at": "2016-11-14T20:26:16.000Z",
        "price": 3.99
      },
      {
        "id": 15,
        "upc": "492840220616",
        "plu": null,
        "name": "Horizon Organic 1% Lowfat Milk (Gallon)",
        "brand_name": "Horizon Organic",
        "brand_type": "1% Lowfat Milk",
        "size": "Gallon",
        "product_image_url": "http://scene7.targetimg1.com/is/image/Target/14937615?wid=1000&hei=1000",
        "created_at": "2016-11-14T20:26:16.000Z",
        "updated_at": "2016-11-14T20:26:16.000Z",
        "price": 7.49
      },
      {
        "id": 84,
        "upc": "300000614048",
        "plu": null,
        "name": "Quaker Cap'n Crunch Crunch Berries Cereal (18.7 oz.)",
        "brand_name": "Quaker",
        "brand_type": "Cap'n Crunch Crunch Berries Cereal",
        "size": "18.7 oz.",
        "product_image_url": "http://target.scene7.com/is/image/Target/13304764?wid=450&hei=450&fmt=pjpeg",
        "created_at": "2016-11-16T20:26:16.000Z",
        "updated_at": "2016-11-16T20:26:16.000Z"
      },
      {
        "id": 91,
        "upc": "073435093305",
        "plu": null,
        "name": "King's Hawaiian Sweet Sliced Bread (16 oz.)",
        "brand_name": "King's Hawaiian",
        "brand_type": "Sweet Sliced Bread",
        "size": "16 oz.",
        "product_image_url": "http://target.scene7.com/is/image/Target/16229584?wid=450&hei=450&fmt=pjpeg",
        "created_at": "2016-11-16T20:26:16.000Z",
        "updated_at": "2016-11-16T20:26:16.000Z"
      }
    ]}]`
