##Objective
The objective of this exercise is to gain experience with Active Record.

##Setup

This folder structure should be suitable for starting a project that uses a database:

* Fork this repo
* Clone this repo
* `rake generate:migration <NAME>` to create a migration (Don't include the `<` `>` in your name, it should also start with a capital)
* `rake db:migrate` to run the migration and update the database
* Create models in lib that subclass `ActiveRecord::Base`
* ... ?
* Profit


## Rundown

```
.
├── Gemfile             # Details which gems are required by the project
├── README.md           # This file
├── Rakefile            # Defines `rake generate:migration` and `db:migrate`
├── config
│   └── database.yml    # Defines the database config (e.g. name of file)
├── console.rb          # `ruby console.rb` starts `pry` with models loaded
├── db
│   ├── dev.sqlite3     # Default location of the database file
│   ├── migrate         # Folder containing generated migrations
│   └── setup.rb        # `require`ing this file sets up the db connection
└── lib                 # Your ruby code (models, etc.) should go here
    └── all.rb          # Require this file to auto-require _all_ `.rb` files in `lib`
```

##Answers
-1) User.count
-2) Item.order(price: :asc)
-3) Item.where(category: 'Books').order("price ASC")
-4) User.joins("JOIN addresses ON users.id = addresses.user_id where addresses.street LIKE '6439 Z%'")
-5) User.joins("JOIN addresses ON addresses.user_id = users.id where users.first_name LIKE 'Virginie'")
          yields id 39
   Addresses.where(user_id:39)update_all(city: 'New York', state: 'NY', zip: '10108')
-6) Item.where(category:'Tool').sum(:price)
-7) Order.sum(:quantity)
-8) Item.joins("JOIN orders ON orders.item_id = items.id where items.category LIKE '%books%'").sum(price * quantity')
-9) User.find_or_create_by(first_name: 'Tiffany', last_name: 'Lewis', email:wantnewbeyalbum@hotmail.com)
   Order.find_or_create_by(item_id:'711', quantity:'1', created_at: '12-12-2013' )



##Notes/Things to Remember
-The databasics file used in this program was also utilized in the SQL Basics repository.
-Remember that you can call multiple methods in one line, but not multiple classes.
-You can access multiple tables.
-Classes are singular and tables are plural.
