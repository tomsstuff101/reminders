# Reminder App

Developed as a team of three in 4 days, to grow skills in Node.js, Express.js and MYSQL.

The app allows individual users to sign on with a dashboard showing their list of reminders and competion deadlines dates. Reminders can be edited and deleted and the user can sign out.


#### Sign-in / Sign-up

<img src="https://github.com/tomsstuff101/reminders/blob/master/README-images/reminder-register.png" alt="sign in and sign up" width="800px" height="auto">


<br>


#### New user

<img src="https://github.com/tomsstuff101/reminders/blob/master/README-images/reminder-signin.png" alt="register new user" width="800px" height="auto">


<br>


#### Desktop Dashboard

<img src="https://github.com/tomsstuff101/reminders/blob/master/README-images/reminder-desktop.png" alt="dashboard for desktop" width="800px" height="auto">


<br>


#### Mobile Dashboard

<img src="https://github.com/tomsstuff101/reminders/blob/master/README-images/reminder-mobile.png" alt="dashboard for mobile" width="300px" height="auto">

---
<br>


## Developement Process
Team spent several hours agreeing how the app should work from the following perspectives

* Endpoints including:
    /register  /signin  /readreminder  /addreminders   /deletereminders   /editreminders   /indextest

* User journey

* User UI

* Database tables and query types

* What data should be set for: addReminder, readReminder, deleteReminder, editReminder


We split into three initial development areas

* Server

* Front-end

* Database


I developed the server code including the fetch requests on the client side. To test them independantly of the front-end code I made a simple test html page to initiate fixed hardcoded requests from the client side on a button click. This is available on the /indextest endpoint

On the server side the server code listened for the fetch requests and using methods defined in app.js responded appropriately.

Stefan created the database and queries, and the sign in front page.
Duncan created the dashboard page, with dynamically created DOM components for the list and acted as the version master,  for all merges from PR's.

Once the intiall code base was formed and modules tested, we worked in a code pairing mannor to ensure all the code smoothly worked across the different parts and iron out any wrinkles.

We also polished up the UI with improved CSS.

---
<br>


## Setup for localhost testing

* Git clone from Github

* install npm dependances

```
$ npm install

```
Now check the package.json that  express, body-parser and mysql are installed.

Note that nodemon is also installed for debugging purposes.

* check if mysql is installed

``` $ mysql --version```

If not installed then install and make sure that the mysql password is the same as the password in the app.js mysql setup object description.

Also make sure that the server is started

eg. For Mac

``` $ sudo /usr/local/mysql/support-files/mysql.server start ```

You should now have a mysql prompt i.e.

``` mysql > ```

#### Create the database

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

#### Start up the app

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







