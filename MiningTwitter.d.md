# Mining Twitter notes

[Book - Mastering Social Media with Twitter: Chapter 2/3](https://play.google.com/books/reader?printsec=frontcover&output=reader&id=XpBNDAAAAEAJ)
[Github](https://github.com/bonzanini/Book-SocialMediaMiningPython/tree/master/Chap02-03)
Local Dir: 
    /Users/jon/code/playground/BE/TweetDigestNotifier/tut/jw

----
## Chapter 2
Export keys
   export TWITTER_CONSUMER_KEY="DtlTKV6Dq3R9FGI0zwo8KoVcD" 
   
Get own timeline, and write jsonl file
    python twitter_get_user_timeline.py jonwhittlestone
    
  ITERABLE = Python object capable of returning it's members one at a time. They include data types such as lists or dictionaries as well as objects ofnany class that implement `__iter__()`
  
  `.jsonl` format means that each line is a vaild json documen`.jsonl` format means that each line is a vaild json document. Useful when using functions that process lines one at a time
  
 ### Streaming
 
 `twitter_streaming.py` includes a class that extends StreamListener and implements the `on_data()` method to write to a `.jsonl` file where each line is a single tweet
 
 Run with:
    python twitter_streaming.py \#Dorking \#SurreyHills
    
----
## Chapter 3

- get followers list
- network analysis and how to use it to mine conversations

endpoint `users/show` given a screen name and returns full profile

180 requests are possible every 15 minutes so not suitable for batch downloads

Better for followers: `followers/list` implemented in Tweepy with `API.followers()` but 1 request per minute rate limit

For batches `followers/ids` can return groups of 5,000 user Ids per request

To get full profile: `users/lookup` with a limit of 180 every 15 minutes



