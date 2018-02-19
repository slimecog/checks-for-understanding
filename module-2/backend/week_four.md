## Week Four Recap

### Instructions
Fork this repository. Answer the questions to the best of your ability.

Try to answer them with limited amount of external research. These questions cover the majority of what we've learned this week.

Note: When you're done, submit a PR with a reflection in the comments about how this exercise went for you.

### Questions

1. What is a cookie?

a cookie is a piece of information saved on a users machine to save state during http transactions.

2. What’s the difference between a session and a cookie?

a session expires on a certain circumstance such as a logout. a cookie has an expiration date.

3. What’s a flash and when do you want to use flashes?

a flash maintains state during a transaction and immediately expires. they are for providing a temporary message to a user.

4. Why do people say “HTTP is stateless”?

each http transaction know nothing about each other. they are separate pieces of information being passed around and maintain no state at all. once it is sent or received it is processed and that is the end of it.

5. What’s authentication? Explain.

authentication the act of verifying one's identity. a log in with a username and password in an example of authentication.

6. What’s the difference between authentication and authorization?

authorization is the act of granting permission(s) to an individual. moderator, admin privileges are an example of authorization.

7. What’s a before filter?

a before filter is a way to force a controller to run a certain action before executing one or many controller actions.

8. How do we keep track of a user once they’ve logged in?

we use sessions to maintain the state of the user being logged in. they expire on logout.

9. When do you want to namespace a resource? When do you want to nest a resource? What's the differences between those two approaches?

you namespace a resource to set the routes for that controller's actions to be set through prefixed path. for example if you namespace admin with a resource nested inside of it, to reach the resource, you would have to go through admin (admin_resource_path(resource)). when you nest a resource you are performing a similar action, however there is a slight difference. you can name space and go through whatever word you choose to use. when you nest you must go through another controller's path to reach the resource you've nested. you would nest a resource if you had an object that belongs to or relies on another object.

10. At a high level, what tools can you use to implement authorization? How would you use them?

you implement authorization by creating a form to log in, having a way to create and save a user, encrypt their password, creating sessions through a session controller. it is helpful to also employ a current_user action in your application controller.

11. What's an enum, and what advantages does it offer? "What data type needs to be in your database to use an enum?" Where do you declare an enum?

enums are a way to provide an attribute to a model without having to create a migration. these attributes are set by naming the attribute on creation of the model object and declaring its value as an integer. enum attributes are zero indexed, so giving the enummed attribute a value of 0 will assign that object the first value names in your enum declaration, which lives in a model. i don't understand "What data type needs to be in your database to use an enum?". an existing model of any sort will do? i don't get it.

12. What are some strategies you can use to keep your views DRY?

html partials, strong params and before filters all help keep code dry.


Reviews Questions
13. Given the following array of hashes, how would I print an alphabetical list of holidays?
```ruby
[
 {holiday: {name: "St Patrick's Day", supplies: ["Corned Beef and Cabbage"]}},
 {holiday: {name: "Halloween", supplies: ["Candy", "Costume"]}},
 {holiday: {name: "Hanukkah", supplies: ["Menorah"]}}  
]
```  

~~after fixing the above to be a valid hash,~~

```ruby
a = [
 {holiday: {name: "St Patrick's Day", supplies: ["Corned Beef and Cabbage"]}},
 {holiday: {name: "Halloween", supplies: ["Candy", "Costume"]}},
 {holiday: {name: "Hanukkah", supplies: ["Menorah"]}}  
]

(a.map { |row| row[:holiday][:name].downcase }.sort).each { |name| puts name }
```


14. How would you clean incoming data to ensure "$300" or "300.00" is stored as 300?
```ruby
data.delete("$.").to_i
```
