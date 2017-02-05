The FoodAdvisorServer is based on a MySQL database and the application is fully implemented in Java.

The <a href="https://github.com/FoodAdvisorProject/FoodAdvisorServer/blob/master/database/DB_SETUP.sql">database design</a> contains three main tables : ARTICLES,USERS,TRANSACTIONS 

- ARTICLES     contains data related to articles
- USERS        contains data related to users
- TRANSACTIONS contains all executed transactions between users involving articles

The <a href="https://github.com/FoodAdvisorProject/FoodAdvisorServer/tree/master/src">Java Application</a> contains four main packages

- classes
- database
- foodadvisor
- users

1. classes contains classes that wil be used in the work flow

2. database contains the interface to the database

3. foodadvisor contains the main that will start our application

4. users contains the routines that will handle client requests and the interface of our app to the world


