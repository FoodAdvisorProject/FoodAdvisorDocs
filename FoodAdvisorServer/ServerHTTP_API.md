#ServerHTTP APIs

The server returns to all the POST methods with OK or the error message associated with the exception.
The server returns to all the GET methods with a JSON Object or the error message associated with the exception.

The main three objects that will be managed are **Articles** , **Users** and **Transactions**.

i suggest you to look at the [DB implementation](https://github.com/FoodAdvisorProject/FoodAdvisorServerDB/blob/master/database/DB_SETUP.sql) to see what attributes are contained in each object.

The server provides the following functions:

* addUser
* getUser

* addArticle
* getArticle

* addTransaction
* getTransaction

* getArticleTravel

* getUserArticles

* getUserIdByEmail


## getTransaction

In order to get a Transaction instance use this function.

- Method: GET /getTransaction
- Fields:
 - tran_id LONG
 
## getArticle

In order to get an Article instance use this function.

- Method: GET /getArticle
- Fields:
 - article_id LONG

## getUser

In order to get an User instance use this function.
NB: this function will be hidden and provided only associated with a session cookie

- Method: GET /getUser
- Fields:
 - user_id LONG
 
## getUserIdByEmail

In order to get an user_id use this function

- Method: GET /getUserIdByEmail
- Fields:
 - email STRING
 
## getUserArticles

In order to get a JSON Array of Articles that belongs to an user use this function

- Method: GET /getUserArticles
- Fields:
 - user_id LONG

## getArticleTravel

In order to get an ordered List of transaction, from the later to the first, use this function.
The creator of the Article has '''seller_id==0''' 

- Method: GET /getArticleTravel
- Fields:
 - tran_id LONG 
 
## addUser

In order to add an user use this function. Note that this will implement the Google NoCAPTCHA to filter robots.
this can be modified later

- Method: POST /addUser
-Fields:
