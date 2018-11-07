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
37 / 52 - Getting Started: Installing BotMan

----
38 / 52 - Getting Started: Installing BotMan

----
39 / 52 - Getting Started: Installing BotMan

----
40 / 52 - Getting Started: Installing BotMan

----
41 / 52 - Getting Started: Installing BotMan

----
42 / 52 - Getting Started: Installing BotMan

----
43 / 52 - Getting Started: Installing BotMan

----
44 / 52 - Getting Started: Installing BotMan

----
45 / 52 - Getting Started: Installing BotMan

----
46 / 52 - Getting Started: Installing BotMan

----
47 / 52 - Getting Started: Installing BotMan

----
48 / 52 - Getting Started: Installing BotMan

----
49 / 52 - Getting Started: Installing BotMan

----
50 / 52 - Getting Started: Installing BotMan

----
51 / 52 - Getting Started: Installing BotMan

----
52 / 52 - Getting Started: Installing BotMan

----

