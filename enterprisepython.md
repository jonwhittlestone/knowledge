# Enterprise Software with Python #
16 Python design patterns

init() shouldn't really do any work, that is up to the caller

----
17 Debugging
Reading traceback: Start at the bottom

Exceptions: everything derives from BaseException

Can either run by dropping a break point or
    python -m pdb yourcode.py   # it will stop when exception is thrown ie. postmortem

in pdb use `pp` to pretty print

pdb: `l` whihch line of code I'm on

----
18 Security

Common mistakes

if you want to secure yourself, a small interface counts. Case in point. Rails vulnerability that allowed execution of Ruby code via yaml

Always santise sensitive data going to logs, Or have a separate log file that contains the important parts

----
19 Code Review

Less than 100 line change, below 20 minutes
https://github.com/mahmoud/espymetrics/pull/2
Common antipatterns
* Don't import more than one type from a function

----
20 Testing
* he uses py.test
* save code from repl where you are doing your
* if you have a demo, make a test for it
* doctest embeds a small test within the docstring

----
21 Logging and Monitoring

How to expose internal state

Provides introspectability
----
22 Profiling and Performance

- time.time()
- timeit - takes average of time. Can be run on command line to measure
----
23 Documentation

"The key to long-term maintenance"

1. design document
2. faq
    - as soon as emails start
3. Developer guide
    * in depth dependencies
    * concernts
    * pull out larger comments
    * link to specific revisions for accuracy

naplinean convention for docstrings

----
24 Packaging, Deployment, Go live

----
25 next steps, how to apply learnings to organisatioj

Justify career growth with 10% time
Find an understaffed team and help out

Underpromise & Overdeliver





