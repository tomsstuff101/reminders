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



## Deploy Reminder app on Heroku and remotemysql.com

TL;DR version

1  Amend code to set the envronment from being localhost to Herokus environment, adding start scripts etc. Ensure that the app is loading up properly in Heroku. It won't function but should install without errors.

2  Create a database in a mysql server. For the purposes of this demo app we use remotemysql.com.

3 Add tables to the database. We used MySQL Workbench, connected to the remote dB and added the tables.

4 Ammend the code (app.js in this case) so that the Mysql connection info correctly matches the remotemysql.com info ie database, username, password etc

``` $ git push heroku master```

The app should now function correctly

#### Detailed version


Befor startting I create a new branch called localhost as I want to have that as a seperate working branch

```
$ git branch localhost
$ git checkout localhost
$ git push origin localhost
$ git checkout master
```

I also create a deploy banch

```
$ git branch deploy
$ git checkout deploy

```
The code can now be ammended

#### package.json

Remove any "test" scripts and replace with
```
...,
"scripts": {
    "start": "node server.js"
  },
  ...

```

##### server.js
create a Port environmental variable

```
// Pull in methods form app.js
const { ......

const app = express()
const port = process.env.PORT || 3019

// define the path ....

```



##### client.js

Ensure that fetch endpoints on the public client side are relative NOT http://;ocalhos etc.
For example 

```

// Sign-in function

const signIn = async () => .....

    let response = await fetch(`/signin?username=${username}`)

    .....

```

You should be able to get teh app to deploy on Heroku at this pint, thou it wont function.

```
$ git checkout master
$ git merge deploy

$ git push heroku master

```

and follow the Heroku deploy link to check.



##### Create remote SQL db

Register on to remotemysql.com and click on 'databases' side tab.
Click on 'create new database'

You will now get a username,database name,password and server name.
Keep this screen handy for copy and pasting

<img src="https://github.com/tomsstuff101/reminders/blob/deploy/README-images/README-MYSQL-info/2%20dB%20created%20-%20copy%20info.jpg?raw=true" width="800" height="auto">
<br>

Using MySQLWorkbench create a new MySQL connection

<img src="https://github.com/tomsstuff101/reminders/blob/deploy/README-images/README-MYSQL-info/3%20create%20a%20new%20db%20connection%20in%20MySqly%20Workbench.png?raw=true" width="800" height="auto">
<br>

Setup a new connection and copy and paste the remotesql data into the 'Setup New Connection' modal. Give it a usefull connection name. Port and default schema shoulod't need changing.

<img src="https://github.com/tomsstuff101/reminders/blob/deploy/README-images/README-MYSQL-info/4%20setup%20a%20new%20connection%20using%20the%20dB%20info%20from%20remotemysql%20.png?raw=true" width="800" height="auto">
<br>



Once the dB has been created in remotemysql.com

##### app.js


```
const connection = mysql.createConnection({
    host: "remotemysql.com",
    user: "ABCD1234",
    password: "WXYZ987",
    database: "ABCD1234"
})


```


Now push to heroku and the app should function properly.

```
$ git push heroku master

```

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







