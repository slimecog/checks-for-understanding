## Week Two - Module 2 Recap

Fork this respository. Answer the questions to the best of your ability. Try to answer them with limited amount of external research. These questions cover the majority of what we've learned this week (which is a TON - YOU are a web developer!!!).

Note: When you're done, submit a PR.

1. At a high level, what is ActiveRecord? What does it do/allow you to do?

ActiveRecord is a tool in ruby for working with SQL. it creates the ORM and gives us built in methods for manipulating the database.

2. Assume you have the following model:

```ruby
class Team << ActiveRecord::Base
end
```

What are some methods you can call on `Team`? If these methods aren't defined in the class, how do you have access to them?

Team.all
Team.count
Team.first.attribute
Team.new
Team.create
etc
these are methods given to us by ActiveRecord

3. Assume that in your database, a team has the following attributes: "id", "name", owner_id". How would you find the name of a team with an id of 4? Assuming your class only included the code from question 2, how could you find the owner of the same team?

Team.find(id: 4) OR Team.find_by_id(4)
if an relationship between owners and teams has not yet been defined, in order to find the owner of given team, you would have to find the owner_id of the desired team and then find the owner with that id.
something like ->
x = Team.find(id: y).owner_id
Owner.find(id: x)

4. Assume that you added a line to your `Team` class as follows:

```ruby
class Team << ActiveRecord::Base
  belongs_to :owner
end
```

Now how would you find the owner of the team with an id of 4?

Team.find(id: 4).owner

5. In a database that's holding students and teachers, what will be the relationship between students and teachers? Draw the schema diagram.

most schools would have a many to many relationship. this is true at turing, as well. students have many teachers and teachers have many students. a join table would be needed.

| teachers |     | students |
| :------- |     | :------- |
| id       |     | id       |
| name     |     | name     |
| module   |     | module   |

      | student-teacher |
      | :-------------- |
      | id              |
      | teacher_id      |
      | student_id      |

6. Define foreign key, primary key, and schema.

a foreign key is need to add an ID from on table to another for a one to many relationship.
a primary key is the ID assigned to a table item on creation.
a schema is the visual representation of your database.

7. Describe the relationship between a foreign key on one table and a primary key on another table.

a primary key on a table will be made a foreign key on a table of which it has many of said table item.

8. What are the parts of an HTTP response?

an HTTP response consists of four parts.
a status line.
a header.
a necessary blank line.
a body.

### Optional Questions

1. Name your five favorite ActiveRecord methods (i.e. methods your models inherit from ActiveRecord) and describe what they do.
2. Name your three favorite ActiveRecord rake tasks and describe what they do.

rake db:test:prepare is nice. sets up the db test environment?

3. What two columns does `t.timestamps null: false` create in our database?

`t.timestamps` is the only necessary part of this line in the current rails version. this creates created_at and updated_at columns in a table and automatically alters the timestamps.

4. In a database that's holding schools and teachers, what will be the relationship between schools and teachers?

usually, this would be a one to many. a school has many teachers and a teacher belongs to a school. however: substitute teachers exist.

5. In the same database, what will you need to do to create this relationship (draw a schema diagram)?
6. Give an example of when you might want to store information besides ids on a join table.
7. Describe and diagram the relationship between patients and doctors.

given the fact that 'doctors' aren't limited to PCPs, this could be a many to many. doctors can include dentists, therapists, etc

8. Describe and diagram the relationship between museums and original_paintings.

one to many. however: original paintings often go on tour. while they can only exists in one place at a time, over a time period they can be in several separate museums.

9. What could you see in your code that would make you think you might want to create a partial?

a repetition in erb or html.
