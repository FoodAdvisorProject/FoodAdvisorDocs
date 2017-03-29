# ServerHTTP APIs

The server returns to all the POST methods with OK or the error message associated with the exception.
The server returns to all the GET methods with a JSON Object or the error message associated with the exception.

The main three objects that will be managed are **Articles** , **Users** and **Transactions**.

Methods with the prefix '''post''' require this header:
Content-Type = application/x-www-form-urlencoded

i suggest you to look at the [DB implementation](https://github.com/FoodAdvisorProject/FoodAdvisorServerDB/blob/master/database/DB_SETUP.sql) to see what attributes are contained in each object.

The server provides the following functions:

* [addUser](#adduser)
* [getUser](#getuser)

* [addArticle](#addarticle)
* [getArticle](#getarticle)

* [addTransaction](#addtransaction)
* [getTransaction](#gettransaction)

* [getArticleTravel](#getarticletravel)

* [getUserArticles](#getuserarticles)

* [getUserIdByEmail](#getuseridbyemail)

## General Notes

In order to get an Article's path we need to identify it as a transaction in which the Article was bought by the User.
This permits to sell the same article to more than one User and avoid confusion between Users

The QR-Code will return a transaction_id, instead of an article_id, that identifies the transaction in which the User has bought the Article.

By default, on each new Article a transaction with seller_id=0 is created. when seller_id=0 the buyer_id is also the id of the article's creator.

Important: 
Note that till now we assume that there aren't evil users, everyone is free to access or create Objects.
In the future this will not be allowed in order to improve our service.
Wherever modification can be done to users instead of using a single user_id we will use a session_cookie that will be produced by a login function.

## Buying an Article

The following steps will be needed to buy an article:
- the buyer **b** scans the Article's QR-Code that provides a transaction id
- the buyer will retrieve the Transaction **t** instance using getTransaction(transaction_id) with the id readed from the QR
- the buyer creates a new transaction filling fields as follow : 
 - article_id = t.article_id
 - seller_id  = t.seller_id
 - buyer_id   = b.user_id
 
From that moment the article will be added to User Articles.

## getTransaction

In order to get a Transaction instance use this function.

- Method: GET /getTransaction
- Return: a JSON Object that represent a [Transaction](#transaction) in case of success, error description in case of error.

TWO METHODS : 

- Fields:
 - tran_id LONG

- Fields:
 - art_id LONG
 - buyer_id LONG 
 
 
## getArticle

In order to get an Article instance use this function.

- Method: GET /getArticle
- Return: a JSON Object that represent an [Article](#article) in case of success, error description in case of error.
- Fields:
 - article_id LONG

## getUser

In order to get an User instance use this function.
NB: this function will be hidden and provided only associated with a session cookie

- Method: GET /getUser
- Return: a JSON Object that represent an [User](#user) in case of success, error description in case of error.
- Fields:
 - user_id LONG
 
## getUserIdByEmail

In order to get an user_id use this function

- Method: GET /getUserIdByEmail
- Return: a long value associated with the user_id
- Fields:
 - email STRING
 
## getUserArticles

In order to get a JSON Array of Articles that belongs to an user use this function

- Method: GET /getUserArticles
- Return: a list [Article](#Article)s in case of success, error description in case of error.
- Fields:
 - user_id LONG

## getArticleTravel

In order to get an ordered List of transaction, from the later to the first, use this function.
The creator of the Article has '''seller_id==0''' 

- Method: GET /getArticleTravel
- Return: a list of Transactions in case of success, error description else.
- Fields:
 - tran_id LONG 
 
## addUser

In order to add an user use this function. 
NB: Note that this will implement the Google NoCAPTCHA to filter robots. this can be modified later.

- Method: POST /addUser
- Fields:
 - login_name STRING
 - login_passw STRING(hash of the function)
 - email  STRING
 - name STRING
 - second_name STRING
 - is_enterprise 1/0
 - enterprise_description STRING
 - photo STRING(BASE64)

# addArticle

In order to add an Article use this function.
NB: This function will dependend only on the session cookie of an user in order to avoid add articles to other users.

- Method: POST /addArticle
- Fields:
 - name STRING
 - creator_id LONG
 - description STRING
 - longitude FLOAT
 - latitude FLOAT
 - photo STRING(BASE64)

# addTransaction

In order to add a Transaction use this function.
NB: the buyer_id will depend only on the session cookie of an user in order to avoid to add transactions to other users.

- Method: POST /addTransaction
- Fields:
 - article_id LONG 
 - buyer_id LONG
 - seller_id LONG
 - longitude FLOAT
 - latitude FLOAT
 
# Transaction
 
contains the following fields :
- buyer_id
- latitude
- longitude
- id
- seller_id
- article_id

# Article

contains the following fields :
- article_id
- name
- creator_id
- description
- photo

# User

contains the following fields :
- user_id
- login
- passw
- email
- name
- second_name
- is_enterprise
- enterprise_description
- photo


