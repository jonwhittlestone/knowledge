# Laravel BotMan #
https://course.buildachatbot.io/course/powerful-conversations/break-out

----
01 / 52 - Getting Started: Installing BotMan

----
02 / 52 - Getting Started: Testing Your Bot

----
03 / 52 - Getting Started: Installing BotMan

----
04 / 52 - Getting Started: Installing BotMan

----
05 / 52 - Getting Started: Installing BotMan

----
06 / 52 - Getting Started: Installing BotMan

----
07 / 52 - Understanding your users: Fallbacks

----
08 / 52 - Getting Started: Installing BotMan

----
09 / 52 - Getting Started: Installing BotMan

----
10 / 52 - Getting Started: Installing BotMan

----
11 / 52 - Getting Started: Installing BotMan

----
12 / 52 - Getting Started: Installing BotMan

----
13 / 52 - Powerful Conversations: Conversation Classes

----
14 / 52 - Powerful Conversations: Validate Conversation Answers

----
15 / 52 - Powerful Conversations: Break Out
- help can be typed anywhere with `skipsConversation()`

----
16 / 52 - Powerful Conversations: Attachments
- When validating, can define a repition method (as a callback) `$this->say('Umm,  this does not look like a valid image to me')`

----
17 / 52 - Powerful Conversations: Buttons
- pass a question object into `ask()` rather than a string

----
18 / 52 - Middleware System: Intro
- https://botman.io/2.0/middleware

----
19 / 52 - Middleware System: Received Middleware
- `class ReceivedMiddleware implements Received {}`
- look at interface definition to indicate we must implement a method called `received(Incoming Message $message, $next, BotMan $bot)`
- define the middleware globaly with `$botman->middleware->received(new ReceievedMiddleware());`
- Cheatsheet: https://laravel.gen.tr/cheatsheet/
- `$message->addExtras('timestamp');`

----
20 / 52 - Middleware System: Heard Middleware

- `class HeardMiddleware implements Heard {}`   // better than `received` middleware bc only triggered when `hears()` is matched 

----
21 / 52 - Middleware System: Sending Middleware

- Gives you the ability to manipulate the payload before it hits the {Facebook|Telegram} server
- `WebDriver::buildServicePayload()`
- good for logging every outgoing message
- can examine response

----
22 / 52 - Middleware System: Captured Middleware
- only used when a user is inside a conversation 

----
23 / 52 - Middleware System: Matching middleware
- allow further control on how you want chatbot users to access certain commands
- copy over method to our middleware implementation and receievs a boolean if a regex was matched
- matching middleware declared at the command level rather than globally with `->middleware(new MatchingMiddleware())`
- `$isAdministrator = $message->getSender() === self::ADMIN_ID;` 

----
24 / 52 - Middleware System: Middleware Groups
kk
- to avoid rewriting multiple `hears()` commands that use the same middleware, can group in a group with `$botman->group(['middleware' => new MatchingMiddleware()], function(){});`

----
25 / 52 - Natrual Language Processing: Introduction

- send the phrase the service and returns structured data
- dialogflow.com

----
26 / 52 - Natrual Language Processing: Setup dialog flow
- https://console.dialogflow.com/api-client/#/getStarted
- can set up test phrases and click on entities / can create events /  weathersearch action
- try it out

----
27 / 52 - Natrual Language Processing: dialogflow middleware

----
28 / 52 - Natrual Language Processing: Using dialogflow middleware
- `$location = extras['apiParameters']['geo-city'];     // receive location from dialogflow middleware rather than the user input`

----
29 / 52 - Botman Playground: Your first playground
- 

----
30 / 52 - Botman Playground

----
31 / 52 - Botman Playground

----
32 / 52 - Botman Playground

----
33 / 52 - Botman Playground

----
34 / 52 - Botman Playground

----
35 / 52 - Create a todobot: Intro
- use draw.io to outline basic tasks http://bit.ly/2Pgptrl

----
36 / 52 - Create a todobot: Show my payees
- show my payees
- create model + db migration with `php artisan make:model Payee -m`

----
37 / 52 - Create a todobot: Add a todo
- 
----
38 / 52 - Create a todobot: Mark a task as finished

----
39 / 52 - Create a todobot: Delete existing todos

----
40 / 52 - Create a todobot: Improving the bot
- add user_id column to table so get todos lists the tasks created by that user and multiple users can use at the same time

----
41 / 52 - Create a todobot: connecting to telegram
- `composer require botman/driver-telegram`
- run ngrok with `~/ngrok http 80`
- https://my.telegram.org/apps 
- `php artisan botman:telegram:register`
- https://web.telegram.org/#/im?p=@tuppencetalkerbot 
- can welcome the new user by `hears('/welcome', function() {});`
- send button and callback to reply - ie button for 'Mark as Completed' with `callbackData()`

----
42 / 52 - Botman on your website: Intro
- add botman webwidet
 
----
43 / 52 - Botman on your website: Associating users
- can pass a userid in javascript to the widget

----
44 / 52 - Botman on your website: programmatic access
- send messages
- https://botman.io/2.0/web-widget#api
- interact with chat widget from `<a href='#' onclick='botmanWidget.say("hi")'>say hi in widget</a>`

----
45 / 52 - Alexa Skill Development: Intro

- https://botman.io/2.0/driver-amazon-alexa
- https://developer.amazon.com/alexa/console/ask
- create custom skill

----
46 / 52 - Alexa Skill Development: Your first skill
- invocation - the name of the skill that you say when you start it
- Define intents
- sample utterances, example sentences that will be said to trigger 
- "Alexa, ask my bank how much is in my account"
- Save Model to train it with utterances,  and build it
- in botman, listen for the intent name
- hook it up by going to endpoint definition - https://developer.amazon.com/alexa/console/ask/build/custom/amzn1.ask.skill.67461022-4dad-48e6-84b3-6af1c0f06833/development/en_GB/endpoint
- can test by speaking into mic on Alexa simulator

----
47 / 52 - Alexa Skill Development: Skill slots
- define another intent to search for conferences with specific languages
- define sample utterances
- custom slots are variables you can use inside of your intents
- access with `$slots = $bot->getMessage()->getExtras('slots');`

----
48 / 52 - Alexa Skill Development: Pre-existing Slot types
- Amazon. slot types are avaiable  like Amazon.EuropeanCity and call the slot 'Location'

----
49 / 52 - Alexa Skill Development: Dialog management
- intent fulfilment to by marking the slot (eg. ProgrammingLanguage) as required so that Alexa can prompt with 'What is the programming language you are interested in'
- botman must do this, Alexa does not do this automagically
- by accessing a dialog state `$bot->getMessage()->getPayload()->get('request')`
- `return $bot->dialogDelegate()`
----
50 / 52 - Facebook Messenger: Getting Started

----
51 / 52 - Facebook Messenger: Getting Started button
- php artisan botman:facebookAddStartButton
- when making changes, in FB, Delete Conversation
----
52 / 52 - Facebook Messenger: Greeting Texts
- 

----

53 / 52 - Facebook Messenger: Persistent menus

