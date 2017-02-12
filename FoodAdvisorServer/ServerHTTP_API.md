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


## getTransaction ( transaction_id :Long )

In order to get 
