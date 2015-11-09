## Sequelize Basics

- Install mysql : `npm i mysql --save`
- Install sequelize: `npm i sequelize --save`

Start the mysql server with: `mysql.server start` and the log in and make a db:

    mysql -u root -p
    create database demo;

After you did that, make a file called `index.js` and put in the following:

    var Sequelize = require('sequelize');
    var sequelize = new Sequelize('demo1', 'root', '', {
      host: 'localhost',
      dialect: 'mysql',

      pool: {
        max: 5,
        min: 0,
        idle: 10000
      },
    });


    var User = sequelize.define('user', {
      firstName: {
        type: Sequelize.STRING,
        field: 'first_name' // Will result in an attribute that is firstName when user facing but first_name in the database
      },
      lastName: {
        type: Sequelize.STRING
      }
    }, {
      freezeTableName: true // Model tableName will be the same as the model name
    });

    User.sync({force: true}).then(function () {
      // Table created
      return User.create({
        firstName: 'John',
        lastName: 'Hancock'
      });
    });

Then run it with `node index.js`

This will create the `user` table and add the user to it. So now if you log back in to your mysql server, you can see the user:

    use demo1;
    show tables;
    select * from user;


## [Sequelize in Practice](http://www.redotheweb.com/2013/02/20/sequelize-the-javascript-orm-in-practice.html)

** Summary coming soon.

### [Transactions](https://github.com/coderbuzz/sequelize-transactions)

A transaction is a batch of table updates. If any step fails, ideally the whole transaction is rolled back. For example, if you take payments and need to set the shipments, you might run a transaction to make sure that the sequence is executed.


