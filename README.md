# Labruska – node.js API for easy e-stores creation

### Just a backend, frontend is up to you

Labruska API is a Node.js/Postgres based Json API for a light or enterprise e-stores. You are free to host your e-store on Express.js or any other Node.js web server or plug it to your existing website.

**It requires Postgres.** Labruska e-store uses its own postgresql db. You are free to add any tables you need for your website or just keep two databases: your own and labruska.

### What can you do with Labruska?

1. Create and search products with any types of attributes.
2. Work with carts and orders.
3. Set custom URL for any page.
4. Write or use existing plugins for shipping, payment, blogging and whatever you need.
5. Create multiple stores on one server with one DB. Multi-tenancy is realized in shared-schema mode.

### Usage examples

##### Get products with filter

```coffee
api = require 'labruska'

query = 
   store_id: 1
   attrs:
      type:     "tablet"
      brand:    ["Apple", "Samsung"]
      os:       "ios"
  page: 1
  perpage: 50
      
api.products.list query, (err, products)->
   console.log products
```

##### Create product

```coffee
product = 
   store_id: 1
   sku: "ph87-13"
   name: "iPhone 6 16 GB"
   attrs:
      type:     "smartphone"
      brand:    "Apple"
      platform: "ios"
      screen:   "750x1334"
  images: ["http://apple.com/iphone6.jpg",
           "http://apple.com/iphone6_back.jpg"]
  price: 820
  price_a: 840 # before discount
  base_price: 750 # supplier's price

api.products.createOrUpdate product, (err, savedProd)->
   console.log savedProd
```

See full API:

- [Stores API](https://github.com/onikonychev/labruska/wiki/Stores-API)
- [Products API](https://github.com/onikonychev/labruska/wiki/Products-API)
- [Product Images API](https://github.com/zalgiris/labruska/wiki/Product-Images-API)
- [Cart API](https://github.com/zalgiris/labruska/wiki/Shopping-Cart-API)
- [Orders API](https://github.com/onikonychev/labruska/wiki/Orders-API)
- [Routes API](https://github.com/onikonychev/labruska/wiki/Routes-API)
- [Lookups API](https://github.com/zalgiris/labruska/wiki/Shopping-Cart-API)
