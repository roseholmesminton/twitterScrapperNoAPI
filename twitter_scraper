# Tweet hashtag based scraper without Twitter API

import mysql.connector
import snscrape.modules.twitter as sntweets
import pandas as pd

pd.set_option('display.max_rows', None)
pd.set_option('display.max_columns', None)
pd.set_option('display.width', 1000)


# query = "python"
# tweets = []
# limit = 100


# for tweet in sntweets.TwitterSearchScraper(query).get_items():
#     if len(tweets) == limit:
#         break
#     else:
#         tweets.append(
#             [tweet.url, tweet.date, tweet.user.username, tweet.content])
# df = pd.DataFrame(tweets, columns=['URL', 'Date', 'User', 'Tweet'])
# print(df)


"""
Establishes a connection to the SQL file database
:return connection object: named db
"""

con = mysql.connector.connect(
    host="localhost",
    user="root",
    passwd="corbla99",
    database="SCRAPER")

mycursor = con.cursor()
# create TWEETS table
# mycursor.execute(
#     "CREATE TABLE TWEETS (HASHTAG VARCHAR(255), USERNAME VARCHAR(255), CONTENT LONGTEXT, URL VARCHAR(255))")

while 1:
    HASHTAG = input('\n\nEnter a hashtag: #')
    max_count = int(input('Enter maximum number of tweets to be listed: '))

    count = 0
    # snscrape uses the given string of hashtag to find the desired amount of
    # tweets and associated info
    for i in sntweets.TwitterSearchScraper('#' + HASHTAG).get_items():
        count += 1
        HASHTAG = HASHTAG
        USERNAME = i.user.username
        CONTENT = i.content
        URL = i.url

        sql = 'INSERT INTO TWEETS(HASHTAG, USERNAME, CONTENT, URL) VALUES(%s, %s, %s, %s)'
        values = [HASHTAG, USERNAME, CONTENT, URL]
        mycursor.execute(sql, values)
        con.commit()
        if count == max_count:
            break

    print('Done!')

    ans = input('Press (y) to continue or any other key to exit: ').lower()
    if ans == 'y':
        continue
    else:
        print('Exiting..')
        break
