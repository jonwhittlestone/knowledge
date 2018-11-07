# Python 10 Apps Notes

The complete document is in Evernote
    https://www.evernote.com/Home.action#n=1d30488f-eea2-45d1-8a9d-ed77690f0574&ses=4&sh=2&sds=5&
----
## App 9:  Real Estate Analysis App

### Vid 1

List Comprehensions and Generator expressions
    These are pythonic operations which allow you to take loops and condense them down to set-based operations
    
More declarative programming rather than procedural

### Vid 5 - Dictionaries

use dictionaries like PHP associative arrays

Like a list but using a key (string, number) to identify, as the index
    my_dict = {}
    
 or just initialise straight away
    my_dict = {‘age’ : 42, ‘location’ : ‘Italy’)}
    
to tell if something is a key that exists
    if ‘cat’ in lookup:
         print lookup[‘cat’]
         
### Vid 8 - - doing arithmetical operations on the data / Lambda expressions

4m 21s
Could pass a function to `data.sort()` or an actual function to retrieve the key
Sorting by price can be done by passing a lambda to data.sort(). A lambda is a little inline method
