# JQuery/Ajax Quiz

Write your answer below each question.

### Question 1
(a) What is a click handler?

A click handler is an event handler that fires when the listener hear a 'click'.

(b) Where in your JS file should you put it, and WHY?

event handlers need to all be referenced in the scope of $(document).ready function, so that the listener has a dom to listen to.

### Question 2
If you get the error `$ is undefined`, what does that mean and what could you do to fix it?



### Question 3
What should go in the `$(document).ready()` part of your JS file?

any chain of JS functions you may want to use in the dom will need to be instantiated somehow within the doc.ready event handler.

### Question 4
In an AJAX GET request, what does the argument of the `.done()` callback - in the example below, that would be `data` - represent?

```
$.ajax({
    url: 'http://ig-hacker-news.herokuapp.com/users',
    type: 'GET',
  })
  .done(function(data) {
    console.log("success!")
  });
```
the argument for done represents the return value of the request. it is the body of the response from the api.the response come usually as JSON, and can be parsed into JS objects.

### Question 5
In an AJAX POST request, what does the argument of the `.done()` callback - in the example below, that would be `data` - represent? (Hint: it's not the same as in Question 4.)

this should be the returned content of the post value itself. for example, if a post request for a new user was made, the .done() argument would be that user object.

```
  $.ajax({
    url: 'http://ig-hacker-news.herokuapp.com/users',
    type: 'POST',
    dataType: 'JSON',
    data: { user: { name: "Anna", about: "instructor", email: "hi@gmail.com" } },
  })
  .done(function(data) {
    console.log("success!");
  });
```
### Question 6
Suppose you had the following form in your HTML file. Use jQuery to write a single line of code that takes whatever the user entered in the textbox and saves it to the variable `user_input`.

```
  <form>
    <p>The dress is:</p><input type="text" id="color">
    <input type="submit" value="Submit" id="submit">
  </form>
```
var user_input = $('#submit').val();

confused here, am thinking that i want a click handler, ie ('#submit').on('click') but with is kinda weird.

### Question 7
This code looks like it works, but when you run it, you see that the `UserApp.add_all_users()` function executes but `console.log` displays `undefined`. What's wrong with the code?

```
UserApp.get_all_users = function() {
  $.ajax({
    url: 'http://ig-hacker-news.herokuapp.com/users',
    type: 'GET',
    dataType: 'JSON'
  })
  .done(function(data) {
    console.log("success!")
    UserApp.add_all_users(data);
  });
};

UserApp.add_all_users = function(data) {
  console.log(data);
};
```


The UserApp.add_all_user(data) needs to be included within the parens to have access to the (data) argument in the .done() function
