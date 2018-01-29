## Week One - Module 2 Recap

Fork this respository. Answer the questions to the best of your ability. Try to answer them with limited amount of external research. These questions cover the majority of what we've learned this week (which is a TON!).

Note: When you're done, submit a PR.

### Week 1 Questions

1. List the five common HTTP verbs and what the purpose is of each verb.

GET - request data from the server
POST - write new data to the server
PUT - full update to existing data
PATCH - partial update of esixting data
DELETE - delete existing data

2. What is Sinatra?

sinatra is a lightweight web framework for ruby similar to rails but with less work done for you.

QUICK QUESTION - why does this list increment correctly on GH but when i clone suddenly this list skips 3???

4. What is MVC?

MVC is the conventional file system configuration for a webapp. Model, View, Controller.

5. Why do we follow conventions when creating our actions/path names in our Sinatra routes?

we follow conventions in developing code to maintain consistency. this enables projects to be worked on by multiple developers and those new to the work by having a familiar platform.

6. What types of variables are accessible in our view templates without explicitly passing them?

ivars.

7. Given the following block of code, how would I pass an instance variable `count` with a value of `1` to my `index.erb` template?

  ```ruby
  get '/horses' do
    erb :index
  end
  ```


  <%= @count %>

  not sure i understand this question. am i supposed to be changing the value of @count or does it hold the value `1` already?

8. In the same code block, how would I pass a local variable `name` with a value of `Mr. Ed` to the view?

<%= @name %>

9. What's the purpose of ERB?

the purpose is to embed ruby in html to have dynamic webpages.

10. Why do I need a development AND test database?

the development database will hold your functional, operating code and the test db will hold pieces not functional yet.
this is a guess.

11. What is CRUD and why is it important?

crud stands for create, read, update, delete. these are the basic functions for storage on a server. without these, a webapp is useless.

12. What does HTTP stand for?

HyperText Transfer Protocol. HTP. this will forever bother me,

13. What are the two ways to interpolate Ruby in an ERB view template? What's the difference between these two ways?

<%= code %> this will render.
<% code %> this will not render.

14. What's an ORM?

an orm is an object relational mapper. the orm we are using currently is activerecord. this is what enables us to interact with our database without having to use raw sql.

15. What's the most commonly used ORM in ruby (Sinatra & Rails)?

activerecord.

16. Let's say we have an application with restaurants. There are seven verb + path combinations necessary to provide full CRUD functionality for our restaurant application. List each of the seven combinations, and explain what each is for.

GET /class Class.all this will get all items pertaining to given class
GET /class/:id Class.find(params[:id]) this is get one item
GET /class/new Class.new this is create a new item
POST /class Class.create(params) this is create a new item
GET /class/:id/edit Class.find(params[:id]) this will get and item to edit
PUT / PATCH /class/:id/update Class.find(params[:id]) && Class.update(params[:id]) this will save new information on existing item
DELETE /class/:id Class.destroy this will delete item of choice

17. What's a migration?

a migration creates a change to the existing database system. create a table, change a table, wtc.

18. When you create a migration, does it automatically modify your database?

not until you write your schema, model and seed file and run ```rake db:create db:migrate db:seed```

19. How does a model relate to a database?

a model tells the database which values are required. i'm not sure what else at this point.

20. What is the difference between `#new` and `#create`?

`#new` makes a new item with given attributes. it does not enter the item into a database.
`#create` makes a new item with given attributes and enters it in a database. it is an alias for `#new` and `#save` run together.

### Review Questions:  
21. Given a CSV file (“films.csv”) with these headers [id, title, description], how would you load these into your database to create new instances of Film?

i would use a ```CSV.foreach``` ```row.to_hash``` method in seeds.rb to enter the entire csv into the table.

22. Given the following hash:
```
activities = {
  hiking: {cost: $0, supplies: ['hiking shoes', 'water', 'compass']},
  karaoke: {cost: $10, supplies: ['courage', 'microphone'],
  brunch: {cost: $35, supplies: ['mimosa flutes'],
  antiquing: {cost: $200, supplies: ['list of antique stores']
}
```
How would I add 'granola bar' to things you should have when hiking?

activities[:hiking][:supplies] << 'granola bar'
ALSO - each line should end in }, OR the end should be }}}}.
EXAMPLE -

```
activities = {
  hiking: {cost: $0, supplies: ['hiking shoes', 'water', 'compass']},
  karaoke: {cost: $10, supplies: ['courage', 'microphone']},
  brunch: {cost: $35, supplies: ['mimosa flutes']},
  antiquing: {cost: $200, supplies: ['list of antique stores']}
}
```

OR

```
activities = {
  hiking: {cost: $0, supplies: ['hiking shoes', 'water', 'compass']},
  karaoke: {cost: $10, supplies: ['courage', 'microphone'],
  brunch: {cost: $35, supplies: ['mimosa flutes'],
  antiquing: {cost: $200, supplies: ['list of antique stores']
}}}}
```

probably the first example. just sayin' :P

23. What are the 4 Principles of OOP? Give a one sentence explanation of each.

abstraction - making real life object in code. classes.
encapsulation - keeping srp inside methods, class, modules etc.
inheritance - the act of inheriting methods and or state from other classes / modules (no state inheritance through modules as they are stateless).
polymorphism - i remember learning that this is the condition of occurring in several different forms but i don't really know what that means in terms of computer science.

### Self Assessment:
Choose One:

* I was able to answer most questions independently, but utilized outside resources for a few

Choose One:
* I feel comfortable with the content presented this week
* I feel overwhelmed by the content presented this week

* i am comfortable as well as overwhelmed.
