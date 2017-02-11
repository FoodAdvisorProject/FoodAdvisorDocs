# FoodAdvisor Server

The FoodAdvisorServer is divided in two main parts:
 - [FoodAdvisorServerDB](https://github.com/FoodAdvisorProject/FoodAdvisorServerDB/)
 - [FoodAdvisorServerHTTP](https://github.com/FoodAdvisorProject/FoodAdvisorServerHTTP/)
 
 
# FoodAdvisor Server DB
[This Repository](https://github.com/FoodAdvisorProject/FoodAdvisorServerDB/) contains the architecture of the database and its interface.

The interface to the database is implemented in Java and the database is implemented using a MySQL database.
We will soon implement a block-chain logic to manage our data if it turn out to be better.

The <a href="https://github.com/FoodAdvisorProject/FoodAdvisorServerDB/blob/master/database/DB_SETUP.sql">database design</a> contains three main tables : ARTICLES,USERS,TRANSACTIONS 

- ARTICLES     contains data related to articles
- USERS        contains data related to users
- TRANSACTIONS contains all executed transactions between users involving articles

The [Java Application](https://github.com/FoodAdvisorProject/FoodAdvisorServerDB/tree/master/src) contains four main packages

- classes
- database
- foodadvisor

1. classes contains classes that wil be used in the work flow

2. database contains the interface to the database

3. foodadvisor contains the main that will start our application

#FoodAdvisor Server HTTP

[FoodAdvisorServerHTTP](https://github.com/FoodAdvisorProject/FoodAdvisorServerHTTP/) Implements the interface to the REST of the world.
Through the functions provided by this module the user will be able to access, add and modify data to our DB

This module is programmed in Scala and depends on Akka-HTTP in order to work
 
1. addUser Example 

POST /addUser

Content-Type: x-www-form-urlencoded

login_name=username&passw_login=passwordhash&email=useremail&name=firstname&second_name=secnd_name&is_enterprise=1&enterprise_description=description&photo=photoinbase64
