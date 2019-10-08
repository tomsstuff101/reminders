# Reminder App


This




#### Sign-in / Sign-up

<img src="https://github.com/tomsstuff101/reminders/blob/master/README-images/reminder-register.png" alt="sign in and sign up" width="1000px" height="auto">



#### New user

<img src="https://github.com/tomsstuff101/reminders/blob/master/README-images/reminder-signin.png" alt="register new user" width="1000px" height="auto">


#### Desktop Dashboard

<img src="https://github.com/tomsstuff101/reminders/blob/master/README-images/reminder-desktop.png" alt="dashboard for desktop" width="1000px" height="auto">



#### Mobile Dashboard

<img src="https://github.com/tomsstuff101/reminders/blob/master/README-images/reminder-mobile.png" alt="dashboard for mobile" width="400px" height="auto">



### Setup for localhost testing

* Git clone from Github

* install npm dependances

```
$ npm install express
$ npm install body-parser
$ npm install mysql

```

* check if mysql is installed

``` $ mysql --version```

If not installed then install and make sure that the mysql password is the same as the password in the app.js mysql setup object description.

Also make sure that the server is started

eg. For Mac

``` $ sudo /usr/local/mysql/support-files/mysql.server start ```

You should now have a mysql promt i.e.

``` mysql > ```

#### Crerate the database

In the mysql prompt cut and past the schema.sql code ie.

``` 

CREATE DATABASE reminder_app 
.
.
.
INSERT ....

```
Now check that the database is installed

```
mysql > SHOW DATABASES;

```

and choose the reminder app database

```
mysql > USE reminder_app;

```

and then have a look at one of the tables e.g.

```

mysql > SELECT * FROM users;

```

Should get a table that looks like

```
mysql > SELECT * FROM users;
+----+--------------+-----------------------+---------------------+
| id | username     | email                 | date_created        |
+----+--------------+-----------------------+---------------------+
|  5 | ben          | benjamin@gmail.com    | 2019-10-03 10:40:14 |
|  2 | dan21        | dan21@legend.com      | 2019-10-03 10:40:14 |
| 46 | fffff        | fffff@ee.com          | 2019-10-03 13:41:44 |
| 47 | yyyyy        | yyyyy@yy.com          | 2019-10-03 14:15:45 |
|  4 | mike         | mike@kgmail.com       | 2019-10-03 10:40:14 |
| 44 | qqqq         | NULL                  | 2019-10-03 13:21:23 |
|  1 | stefanG      | stefan@codenation.com | 2019-10-03 10:40:14 |
|  3 | tom          | tom@CN.com            | 2019-10-03 10:40:14 |
| 45 | wwwww        | NULL                  | 2019-10-03 13:24:02 |
|  6 | foobar       | foo@barbar.com        | 2019-10-03 11:13:06 |
+----+--------------+-----------------------+---------------------+

```

Open up another bash shell

```
$ node server.js
```

this should give

```
listening to localhost:3019

```


Now open up a browser at localhost:3019

and the sign-in screen should be displyed with a number of users e.g. 10 shown

<img src="https://github.com/tomsstuff101/reminders/blob/master/README-images/reminder-register.png" alt="sign in and sign up" width="500px" height="auto">



reminder-mobile





