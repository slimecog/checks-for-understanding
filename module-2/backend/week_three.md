## Week Three Recap

### Instructions
Fork this repository. Be sure to pull the latest changes to your local repo. Answer the questions to the best of your ability.

Try to answer them with limited amount of external research. These questions cover the majority of what we've learned this week.

Note: When you're done, submit a PR with a reflection in the comments about how this exercise went for you.

### Questions

1. What is the entry at the command line to create a new rails app?

rails new project_name -T -d="postgresql" --skip-turbolinks --skip-spring

2. What do Models generally inherit from in rails?

ApplicationRecord

3. What do Controllers generally inherit from in a rails project?

ApplicationController

4. How would I create a route if I wanted to see a specific horse in my routes file assuming I'm sticking to standard conventions and that I didn't want other CRUD functionality?

`resources :horses, only: [:show]` in config/routes.rb
`def show
  @horse = Horse.find(params[:id])
end` in horses controller

5. What rake task is useful when looking at routes, and what information does it give you?

`rake / rails routes` this shows the uri routes you have available

6. What is an example of a route helper? When would you use them?

a route helper would be using `horse_path(horse)` to view a page rather than hand writing the route like `/horses/:id`
i use them any time i need to express a route. to me it seems more universal and is also explicit.

7. What's the difference between what `_url` and `_path` return when combined with a routes prefix?

not too sure about this one. from my understanding you should use `_url` when you need to redirect to a specific uri, however i've been using `_path` and haven't had any problems. it also seems like a convention to use `_url` in the controller and `_path` in views.

8. What are strong params and why are they necessary?

strong params allow us to define exactly which attributes we are going to use when creating a new object in our database. we use them to take logic out of our controller actions.

9. What role does `form_for` play in helping us create our forms?

`form_for` allows us to create an html form in erb. it allows us to iterate through a collection and create entry boxes for creating new, or updating existing objects in a view page on our app.

10. How does `form_for` know where to submit the user's input?

based on the action that rendered the view a form lives in. we use ivars in the action and based on the action and ivar, the information is entered in the database based on the http verb used.

11. Create a form using a `form_for` helper to create a new `Horse`.

horse controller
`def new
  @horse = Horse.new
end`
horse new view
`<%= form_for @horse do |f| %>
  <%= f.label :name %>
  <%= f.text_field :name %>
  <%= f.submit %>
<% end %>`
horse create action would be run next and might look something like
`def create
  @horse = Horse.new(horse_params)
  if @horse.save
    flash[:success] = "#{@horse.name} successfully added"
    redirect_to horse_path(horse)
  else
    render :new
  end
end`

12. Why do we want to validate our models?

we validate our models to ensure that certain attributes are present on creation. for instance, when registering a new user on a page, we for certain need to have at least an email and password so they can return to their profile next time they visit the page to log in. we would `validate_presence_of :email, :password` and should also `validate_uniqueness_of :email` to ensure the user hasn't already created an account.
