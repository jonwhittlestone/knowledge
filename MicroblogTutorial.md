# Flask Microblog Tutorial

url: https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world
working dir: /Users/jon/code/playground/BE/microblog

----

## 01/18 Hello World

Create a private version of your python interpreter insider a folder called 'flask'
    ▶ python3 -m venv flask

Create an init script for our app package which imports the views module (among other things)

Create run.py to start up the development web server

    playground/BE/microblog  jons-dotfiles-repo ✗                                                              42d ⚑ ✚ ◒
    ▶ ./run.py
     * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
     *  * Restarting with stat
     *  * Debugger is active!
     *  * Debugger PIN: 842-858-270
     * 127.0.0.1 - - [21/Sep/2017 16:28:00] "GET / HTTP/1.1" 200 - 

## 02/18 Templates
Use `render_template()` to invoke the Jinja2 template engine
Can use control statements `{% if title %}`<title>Great</title> etc
Can use loops also
    {% for post in posts %}
            
Template inheritance: Use block control statement to insert entire templates

## 03/18 Web Forms
* using Flask-WTF
* setup {root} / config.py
* created a form for Login which uses openid
* methods argument in route director tells FLask that the view function accepts GET and POST [requests](requests)
* `get_flashed_messages()`

## 04/18 Database

## 05/18 User Logins

## 06/18 Profile Page & Avatars

## 07/18 Unit Testing

## 08/18 Followers, Contacts and Friends

## 09/18 Pagination

## 10/18 Full Text Search

## 11/18 Email Support

## 12/18 Facelift

## 13/18 Dates and Times

## 14/18 I18n and L10n

## 15/18 Ajax

## 16/18 Debugging, Testing and Profiling

## 17/18 Deployment on Linux

## 18/18 Deployment on Heroku
