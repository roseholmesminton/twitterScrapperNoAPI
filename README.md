# twitterScrapperNoAPI

Tweet hashtag based scraper without Twitter API

Adapted from the book: 53 Must Do Pythong Projects For All by Edcorner

In this project I learned how to use snscrape to scrape tweets associated with a particular hashtag.
Snscrape is a python library that scrapes twitter without the use of API keys. 
To test that snscrape worked, first I searched using a keyword "python" and added the results to a list named tweets (This code is commented out)
Next, I created a mySQL db named scraper and I created a table named tweets in the database
Finally, I searched twitter based on a hashtag that is the user is prompted to enter along with the maximum number of records
The tweets are fetched by snscrape and stored in the database (I used mySQL Workbench 8. The textbook uses SQLite3),
I am storing the hashtag, the tweet content, user id, as well as the URL of the tweets in the database.
