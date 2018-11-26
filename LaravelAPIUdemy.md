# RESTful API with Laravel: Definitive Guide #
- https://www.udemy.com/restful-api-with-laravel-php-homestead-passport-hateoas/learn/v4/overview
- https://github.com/JuanDMeGon/RESTful-API-with-Laravel-Definitive-Guide

ERD for sample app
i https://raw.githubusercontent.com/jonwhittlestone/knowledge/master/assets/laravel-api-annotated-erd-purchasing-system.png

## Intro ##

----
## Section 2 - How to download and install tools ##

### 02-04 - virtualbox ###
### 02-06 - vagrant ###
### 02-07 - install sublime ###
### 02-08 - github shell ###
### 02-09 - install node/npm ###
### 02-10 - install postman ###
### 02-11 - obtaining Laravel with composer ###

----
## Section 3 - Creating and setting initial structure ##
- completed
----
## Section 4 - Configuring and using Sublime Text 3 ##
- completed
----
## Section 5 - Understanding the Case Study ##
- https://github.com/jonwhittlestone/knowledge/blob/master/assets/laravel-api-annotated-erd-purchasing-system.png
- create a list of every endpoint


----
## Section 6 - Discovering and configuring the Laravel structure ##
- 
### 06-25 - Laravel structure ###
### 06-26 - artisan commands ###
### 06-27 - Laravel environment variables ###
### 06-28 - understanding routes ###
- 'api' prefix in `RouteServiceProvider::mapApiRoutes`
- 

----
## Section 7 - Creating the intitial Laravel components ##

### 07-30 - Intial Laravel structure ###
- first, create the model with the migration, the controller comes later
- likely that every model you have is a resource in your RESTFUL api
- buyer and seller extend directly from user


### 07-31 - creating stucture for controllers ###
- controllers for respective resources
- `php artisan make:controller Buyer\BuyerController -r`

### 07-32 - creating endpoint with routes ###
- https://github.com/JuanDMeGon/RESTful-API-with-Laravel-Definitive-Guide/commit/7a89b43a55891a448134028a739104796e9b8767

- `php artisan route:list` to see which routes have been created

 
----
## Section 8 - Implementing the RESTful API Models ##

### 08-33 - implenting the properties for category  ###
- `protected $fillable = []`


### 08-34 - implementing properties for product ###
- https://github.com/JuanDMeGon/RESTful-API-with-Laravel-Definitive-Guide/commit/a72516d9672fc1b85c1f18184d77028fa69f8e3b
- use contstants in the code
- `const AVAILABLE_PRODUCT = 'available';`
- write model method - `isAvailable()`

### 08-35 - properties for transaction ###
- https://github.com/JuanDMeGon/RESTful-API-with-Laravel-Definitive-Guide/commit/803c1d588fc0108565ec2299d58c797bd028745e


### 08-36 - The properties of a user ###
- add attribute `hidden`
-  https://github.com/JuanDMeGon/RESTful-API-with-Laravel-Definitive-Guide/commit/35f8e284d457f3020f8d0170f3e8227a38738ce5
- adding, `isVerified()`, `isAdmin()`, `generateVerificationCode()`
- `generateVerificationCode` can be a static method as it's executed from the model

### 08-37 - Implemnting the relationships between the model ###

- https://github.com/JuanDMeGon/RESTful-API-with-Laravel-Definitive-Guide/commit/722d116395d4b897140b9cc580c834e3e3c0978d
- a buyer has several transactions = `return $this->hasMany(Tranaction::class);`
- Does VIM support auto importing
- A product can have many categories / a category can have many products `$this->belontsToMany(Product::class);`
- how do you know who belongs to who? the model that has the foreign key, is model that `BelongsToMany`

----
## Section 9 - Creating the DB structure using migrations ##


### 09-38 - solving a common issue with migrations  ###
- utf8mb4 mysql charset
- default string length
- `Schema::defaultStringLength(191);`

### 09-49 - implementing migration for users  ##
- https://github.com/JuanDMeGon/RESTful-API-with-Laravel-Definitive-Guide/commit/8c87dc727c712c076ca3f40cb35a16263436059c

### 09-40 - categories migration  ##
### 09-41 - products migration ##
### 09-42 - transactions migration ##
### 09-43 - pivot table  ##
- https://github.com/JuanDMeGon/RESTful-API-with-Laravel-Definitive-Guide/commit/5caf5ad4b3a555ddf35d545cb892f8b0554c13aa 
- for many to many relationship
- `php artisan make:migration category_product_table - --create=category_product`
- note: singular, category_product
- don't need timestamps and kist add foreign keys as usual

----
## Section 10 - Creating the Laraval Factories for Database Seeding ##


### 10-44 - Create the laravel factory for the user  ##
- https://github.com/JuanDMeGon/RESTful-API-with-Laravel-Definitive-Guide/commit/efca530f417d465d400174c9963db57cde694fd6
- user faker to randomly select items from an array

### 10-45 - Creating the factory for category  ##
### 10-46 - Creating the factory for product  ##
- assign an image with `$aker->randomElement(['1.jpg','2.jpg'])`
### 10-47 - Creating the factory for transaction  ##
- https://github.com/JuanDMeGon/RESTful-API-with-Laravel-Definitive-Guide/commit/efca530f417d465d400174c9963db57cde694fd6
- `$seller = Seller::has('products')->get()->random();`

### 10-48 - using the factories in the seeder  ##
- https://github.com/JuanDMeGon/RESTful-API-with-Laravel-Definitive-Guide/commit/0d4a69b84d2a246dc0b6c189280a93bd3d9d8d28
- whenever seeder is run, truncate all tables
- disable foreign key checks with `SET FOREIGN_KEY_CHECKS=0`

### 10-49 - executing migrations and seeder with artisan  ##


----
## Section 11 - Implementing the Operations for UserController ##

### 11-50 - Implementing the index action on user controller  ##

### 11-51 - UserController@show  ##

### 11-52 - UserController@store  ##
- https://github.com/JuanDMeGon/RESTful-API-with-Laravel-Definitive-Guide/commit/b213b2102ccf952e9cd76370b5880d30e1c13dd3
- 201 status code meaning 'created'

### 11-53 - UserController@update  ##



----
## Section 12 - Implementing the operations for Buyer ##

----
## Section 13 - Implementing the operations for Seller ##

----
## Section 14 Improving the current RESTful API operations ##

 
### 14-59 - Defining mutators and accessor for models  ###
- https://github.com/JuanDMeGon/RESTful-API-with-Laravel-Definitive-Guide/commit/92ea2b569f8dce5ee3edb0330f6c643324ff5307
- return transformation so eveything is uppercase/lowercase

### 14-60 - generalising the response methods  ###
- create API controller
- https://github.com/JuanDMeGon/RESTful-API-with-Laravel-Definitive-Guide/commit/7801ff0649afd8a0813d3f5e55106d60544614b9
- store all our traits in trait folder
- ApiResponser.php

### 14-61 - using generalised methods  ###
 - https://github.com/JuanDMeGon/RESTful-API-with-Laravel-Definitive-Guide/commit/116ab5bf85754de02909eda3fea65168ab0be59a


### 14-62 - using generalised methods for error response  ###
- https://github.com/JuanDMeGon/RESTful-API-with-Laravel-Definitive-Guide/commit/e41baf216853f17279007dd8f167a738a08d9590


----
## Section 15 - Handling Errors and Exceptions with the Laravel Handler ##


### 15-63 - returning validation errors in responses  ###
- `App\Exceptions\Handler.php`
- https://github.com/JuanDMeGon/RESTful-API-with-Laravel-Definitive-Guide/commit/7a0b17de693815e1be58a2e131c82008ea8fba60
- modify te render method by redefining how it is defined in the parent class `convertValidationExcetionToResponse`
- use the trait to then return as function `errorRespones` from `ApiResponser` trait create in 14-60

### 15-64 - Model not found exceptions as JSON response  ###
- add a new condition to `App\Exceptions\Handler::render()`
- https://github.com/JuanDMeGon/RESTful-API-with-Laravel-Definitive-Guide/commit/470e57ba32d605f2f9f73065454f6ce8891cca80

### 15-65 - Handling Authentication exception  ###
- https://github.com/JuanDMeGon/RESTful-API-with-Laravel-Definitive-Guide/commit/5d7587fbf659185428588e6cfe5ed36d8f22238b

### 15-66 - Handling Authorisation exception  ###
- if a user does not have permission
- https://github.com/JuanDMeGon/RESTful-API-with-Laravel-Definitive-Guide/commit/4fb76a7aeba2bbfeb4a4bfe931ba83179bd16f7c

### 15-67 - Handling NotFoundHttpException  ###
- try to access the wrong url, catch a different exception
- add new condition to `render()` method
- https://github.com/JuanDMeGon/RESTful-API-with-Laravel-Definitive-Guide/commit/abebc5a22eb04696ef4ec777a683b46e9e4a892e

### 15-68 - Handling `methodNotAllowedHttpException`  ###
- https://github.com/JuanDMeGon/RESTful-API-with-Laravel-Definitive-Guide/commit/096882e7ffe8a48e034000a8dd436491f5a620b1

### 15-69 - Handling GeneralHTTPException  ###
- if any other http exceptions aren't caught..

### 15-70 - catching specific exceptions  ##
- https://github.com/JuanDMeGon/RESTful-API-with-Laravel-Definitive-Guide/commit/968686a37c6b19ee37df2d446e3aee6c571ce25b
- use dd() to get code and handle specific exceptions

### 15-71 - unexpected exceptions  ##
- return an `errorResponse('unxpected exception', 500);`
- only if we are in production
----

## Section 16 - Implicit Model Binding with Routes and Methods ##

### 16-72 - implicit model binding  ##
- instead of method using the $id
- https://github.com/JuanDMeGon/RESTful-API-with-Laravel-Definitive-Guide/commit/fc75235cc633815864f7baafbb0134c5483f2c05


### 16-73 - resolving Buyer using Laravel Global scopes   ##
- automatically apply has('transaction') query that can be automatically add
- create a scopes directory
- https://github.com/JuanDMeGon/RESTful-API-with-Laravel-Definitive-Guide/commit/ad120a9529723bd69de08f9b2bebcba420fd9a6e
- https://laravel.com/docs/5.7/eloquent#query-scopes


----
## Section 17 - Implementing SOft Deleting for All the Models ##

----
## Section 18 - Implementing the Operations for the Category ##

----
## Section 19 - Implementing the operations for the product ##

----
## Section 20 - Exercies - Implementing the Operation for Transaction ##

----
## Section 21 - Implemtning Complex operations within Transaction ##


----
## Serction 22 - Implementing Complex operations for buyer ##

----
## Section 23 - Implementing complex operations for category ##

----
## Section 24 - Implemnting Complex operations for Seller ##

----
## Section 25 - Implementing complex operations for product ##

----
## Section 26 - Adding an image for Products ##


----
## Section 27 - Sending Email for Users Accounts Verification ##

----
## Section 28 - The middleware and the rate limiting###

----
## Section 29 - Transforming Responses with PHP Fractal for Security and Compatibility ##

----
## Section 30 Sorting and Filtering reslts based on Query parameters ##

----
## Section 31 - Pagination of Results ##

----
## Section 32 - caching results with laravel cache system ##


----
## Section 33 - Implementing HATEoAS hypermedia controls ##


----
## Section 34 - Transformations and Validations ##

----
## Section 35 = preparing the API for User Authentication using sessions ##


----
## Section 36 Using Laravel Passport to Implement the Initial Security Layer with OAuth2 ##


----
## Restricting oAuth2 clients using scopes ##

----
## Section 38  - Final security layer using policies and gates of Laravel ##


----
## Section 39 - CORS for Laravel ##

----
## Section 40 - 43 Upgrading / Conclusion ##

