Questions from Week 5:
1. How do we make flash messages display on a page?

we make flash messages display to the page by adding a flash[:key] = "notice" in an action and by parsing through the flash hash in the application controller

2. Where is cart information/temporary information usually stored?

temporary information is stored in a session. this includes carts and user login state.

3. What might be some reasons not to store a cart in our database? Are there any reasons why we would want to persist that information?

it would be a bad idea to store a cart in the database because the next user who logs in will have another user's items in their cart. you want to persist cart information to maintain the state of the cart throughout user activity within the application. if the state of the cart did not persist, once you visit any page after adding an item to your cart, the cart would no longer hold any items.

4. What is the purpose of the asset pipeline?

the purpose of the asset pipeline is to provide a hierarchy for the order in which styles are compiled and loaded.

5. Why do we precompile our assets?

the purpose of precompiling assets is to concatenate and minify our js and css. it makes your webapp load much more quickly.


6. What do each of the following tags do?

```
<%= stylesheet_link_tag "application" %>

this will include the application.css stylesheet

<%= javascript_include_tag "application" %>

this will include the application.js stylesheet

<%= image_tag "rails.png" %>

this will include images in the assets/images directory
```

7. What are some of the elements of a great read me? What are some of the benefits of taking the time to update a readme for our project?

some elements of a great readme include a project summary, installation instructions, deployment instructions, how to contribute, links to relevant docs, how to test, contributors etc. the benefits include educating a potential user on what your project is / is for. no one will use a code base if they don't even know what does!

8. What are the top four accessibility issues that we as developers should be aware of?

visual, auditory, mobility and cognitive impairments.

9. `before_save` is an example of a what? Where in our Rails application would we find a `before_save`?

before save is an example of a filter? (or is it a callback? gotta do some research on the difference). this would live in a specific controller or in the application controller if it's purpose is overarching for all controllers.

10. Given the following object, how would we create a scope for all users who are active?

```ruby
User.create(name: "Happy", active: true)
```

scope :active, -> { where(active: true) }

11. What is the difference between a scope and a class method?

scopes are for returning a certain type of information if there are any matches to the parameters you define, otherwise it returns all. class methods are better for when you need more complex logic.

Review Questions:  
12. Given the following hash:  

```ruby
{cart: {"17" => 4, "204" => 52, "29" => 22}}
```

  12a. How would you add item with id of 48 with a quantity of 4?

  ```ruby
  given[:cart]["48"] = 4
  ```

  12b. How would you increase the quantity of item 29?

  ```ruby
  given[:cart]["29"] += increase_amount
  ```

  12c. How would you find out how many items your user is thinking about purchasing?

  ```ruby
  given[:cart].values.sum
  ```

13. What is polymorphism? How does it relate to duck-typing? What are two ways you use this in everyday Rails applications?

polymorphism is the condition of being (or acting like) two things at once. "looks like a duck, quacks like a duck..." an example of polymorphism in rails is that many rails methods use or return objects that look and act like arrays or hashes, but are in fact not an actual array or hash object. many methods available to arrays or hashes will be available to these objects but not necessarily all methods.

14. How would you clean the string "(630) 854-5483" to "630.854.5483"?

```ruby
string.delete("/(/)").gsub!(/[- ]/,".")
```
