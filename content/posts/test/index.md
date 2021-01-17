---
title: Twitter Sentiment Analysis in Python
subtitle: Part 1 - Downloading Twitter Data using Tweepy

# Summary for listings and search engines
summary: Welcome 👋 We know that first impressions are important, so we've populated your new site with some initial content to help you get familiar with everything in no time.

# Link this post with a project
projects: []

# Date published
date: "2021-01-15T00:00:00Z"

# Date updated
lastmod: "2021-01-15T00:00:00Z"

# Is this an unpublished draft?
draft: true

# Show this page in the Featured widget?
featured: false

# Featured image
# Place an image named `featured.jpg/png` in this page's folder and customize its options here.
image:
  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/8cMPxOqkLE8)'
  focal_point: ""
  placement: 1
  preview_only: false

authors:
- cam

tags:
- Sentiment Analysis 
- Twitter
- Tweepy
- Python

categories:
- Sentiment Analysis
---

2nd post - image https://unsplash.com/photos/auEPahZjT40
### Some background

Late last year I had a horrible time trying to buy a Google Pixel 5 online from Currys PC World, the UK's largest electrical retailer. The phone came with a free set of Bose headphones worth £300 so I was excited to make the purchase and paid £10 extra for next day delivery. When the phone didn't arrive the next day and I hadn't heard anything, I rang Currys' customer service team to find out why.

Currys' customer service team is called Team Knowhow which is ironic considering every time I called they had absolutely no idea about anything to do with my order. Each time I called I would wait about an hour on hold before someone different would answer and give a different reason for what had happened and why my order hadn't been delivered. The person would then tell me that I would be called back within 24-48 hours to resolve the issue, which of course never happened, forcing me to call back, wait on hold again and have the whole process repeat multiple times.

After a week of calling and still with no phone, I was frustrated and searched online for other ways to contact Team Knowhow. I first found an email address so I sent all my details but never got a reply. To be fair, eventually I did get a reply but it only arrived last week, nearly 3 months to the day from when I had sent my first email. 

I also found Team Knowhow's Twitter account which had lots of activity back and forth between customers and the Team Knowhow customer support team. I've had a Twitter account for years but apart from tweeting to enter the occasional competition, I've never really used it other than a source of news and information. I noticed others having the same issue as me so I tweeted for help.


```python
import requests
from IPython.display import HTML
response = requests.get('https://publish.twitter.com/oembed?url=https://twitter.com/cammclean182/status/1319898794830536705')
html = response.json()["html"]
display(HTML(html))
```


<blockquote class="twitter-tweet"><p lang="en" dir="ltr">I paid for a <a href="https://twitter.com/Google?ref_src=twsrc%5Etfw">@Google</a> Pixel 5 online from <a href="https://twitter.com/curryspcworld?ref_src=twsrc%5Etfw">@curryspcworld</a> which was available for next day delivery and they haven&#39;t delivered. They have taken my money but won&#39;t tell me when it will be back in stock. <a href="https://twitter.com/TeamKnowhowUK?ref_src=twsrc%5Etfw">@TeamKnowhowUK</a> isn&#39;t responding to my calls or emails. Very frustrating.</p>&mdash; Cameron McLean (@cammclean182) <a href="https://twitter.com/cammclean182/status/1319898794830536705?ref_src=twsrc%5Etfw">October 24, 2020</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>



@TeamKnowhowUK replied pretty much straight away and asked me to direct message them more information so they could look into it. Unfortunately it turned out the Team Knowhow service on Twitter wasn't any better than the Team Knowhow service via phone. After I sent them all the information, they would say they were looking into it and then never respond to any future messages sent via DM. Each time I followed up for an update my messages got ignored. I'd then tweet again publicly which would get an immediate response, again asking me to DM them my information which would then get ignored and the process would repeat.

I was more than frustrated and tweeted them to let them know how I felt.

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">I love how <a href="https://twitter.com/TeamKnowhowUK?ref_src=twsrc%5Etfw">@TeamKnowhowUK</a> ask you to DM them for &#39;privacy reasons&#39; but when you do they still don&#39;t respond or resolve your issues. It seems like they want to appear to help but really they just want people to contact them privately where the public can&#39;t see them ignore you.</p>&mdash; Cameron McLean (@cammclean182) <a href="https://twitter.com/cammclean182/status/1320332221530648576?ref_src=twsrc%5Etfw">October 25, 2020</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

To cut a long story short, there's some truth in the proverb about the squeaky wheel getting the grease. After tweeting publicly a few times to highlight @TeamKnowhowUK's terrible customer service, there was eventually a happy ending and my new phone was delivered a few weeks later. I never received an explanation about what had happened with my order but from other complaints I've read online, it looks like Currys' online store struggles to keep track of what's in stock and has a long history of selling out of stock items they can't deliver. Despite the happy ending I made a promise to myself that i'd never shop at Currys again.

### So what's this got to do with Sentiment Analysis in Python?

Recently I've been experimenting with some sentiment analysis libraries in Python. Sentiment analysis, or opinion mining, refers to the use of natural language processing to systematically analyse large quantities of unstructured text and identify whether the text has positive, negative or neutral sentiment. 

Sentiment analysis is commonly used by businesses to conduct market research and analyse how products, competitors or customer support are perceived by the market. I've also read it's used by quantitative hedge funds who have incorporated sentiment analysis into trading strategies. I was keen to understand the process better to then see how I could apply it to my own trading strategies.

A common source of data for sentiment analysis is Twitter which led me to expirement with some libraries used for downloading Twitter data, mainly Tweepy and Twint. When looking for data to analyse, I remembered my experience with Team Knowhow and the negative sentiment I saw in all the tweets from unhappy customers. I wondered whether the sentiment analysis libraries would report the same.

### Twitter Data Libraries - Twint vs Tweepy

To download data from Twitter there seems to be two main Python libraries - [Twint](https://github.com/twintproject/twint) and [Tweepy](https://www.tweepy.org/).

I first started using Tweepy which uses Twitter's official API to access and download data. It requires you to apply for developer access to get keys from Twitter to use their API which is relatively quick and painless. As the library has been around for over 10 years, the documentation is great and there are plenty of tutorials online for learning how to use the package.

The main advantage of using Tweepy is that it uses the official Twitter API. This enables much more functionality than just downloading tweets. You can post tweets, block people, send DMs and write scripts to automatically retweet or follow back people who follow you. 

The biggest limitation of Tweepy is also that it uses the official Twitter API. The API limits the amount of data that can be downloaded and with the free account you are limited to downloading a few thousand tweets from within the last 7 days. This is great for obtaining recent data but for some of the trading ideas I wanted to explore, I would need tweet data going back further in history to conduct proper backtests.

Twint is a much younger library and the documentation is somewhat minimal. It doesn't use the official Twitter API to obtain data but rather scrapes Twitter from public webpage addresses. Once you get it installed correctly (see below), its performance seems to be on par with Tweepy and it downloads data just as quick. It's never going to be as fast as using the offical API but its biggest advantage from not using the API is that you can effectively download tweets going back as far as you want, without any rate limitations.

Both libraries are popular and work well but Twint has recently taken the lead in Github stars, I assume from data hungry scientists looking to obtain tweet data older than the last 7 days.  

<img src="images\starhistory.png">
<div style="text-align: center"> Github Star History: https://star-history.t9t.io/#twintproject/twint&tweepy/tweepy </div>


### Installation of Twint

Despite online installation instructions advising a simple `pip install twint` to install Twint via PyPI's repository, I immediately ran into issues trying to use the library. It looked like Twitter had removed one of the endpoints that Twint used to make searches. 

Googling for solutions, I found the issue being discussed on [Twint's github repo](https://github.com/twintproject/twint/issues/915) and one of the contributors Himanshu Dabas providing a workaround that could be installed directly from Twint's github repo:

`pip install --upgrade git+https://github.com/twintproject/twint.git@origin/master#egg=twint`

Note if you are using Windows you'll also need Microsoft's C++ build tools to be installed.

To use Twint in Jupyter notebooks you also need to install nest asyncio by:

`pip install nest_asyncio`

### Searching Twitter using Twint

Before using Twint you need to import the twint and nest_asyncio libraries and then apply nest_asynicio to allow event loops to be nested.


```python
# import required libraries
import twint
import nest_asyncio
nest_asyncio.apply()
```

Once eveything is imported you need to specify your configuration parameters for the search function.

There's dozen of options that allow you to make your searches as simple or complex as required. You can search for tweets containing a specific keyword or username and you can use combinations of multiple paramaters to do complex searches such as finding tweets with a specific keyword that have more than 100 likes and were tweeted from a specific location on a specific date. 

There's also configuration options to specify how you want to store the results, whether that be in a JSON file, CSV or SQLite Database. 

A full set of configuration options can be found on [Twint's Github Wiki](https://github.com/twintproject/twint/wiki/Configuration).


```python
# twint configuration
c = twint.Config()

c.Search = 'teamknowhowuk'

c.Since = '2020-10-01 00:00:00' #"2020-10-01 00:00:00"
c.Until = '2020-10-02 00:00:00' #"2020-11-01 00:00:00"
 
c.Hide_output = True

c.Store_json = True
c.Output = '../data/twint_search_data.json' #outpath 
```

Above I used the 'since' and 'until' configuration paramaters to search for tweets in October 2020. Despite the docs saying otherwise, I found that the dates had to be passed in using the following format '%Y-%m-%d %H:%M:%S'.

I've also set Hide_output to True to hide the scraper showing each tweet as it searches which quickly fills up the window when doing the search in Jupyter notebooks.

Once you have specified the configuration paramaters, they can then be passed into the Search function.


```python
Path.PurePath('data','test.json')
```


    ---------------------------------------------------------------------------

    AttributeError                            Traceback (most recent call last)

    <ipython-input-24-0483da28d5e7> in <module>
    ----> 1 Path.PurePath('data','test.json')
    

    AttributeError: type object 'Path' has no attribute 'PurePath'



```python
from pathlib import Path
outpath = (Path.cwd().parent / 'data' / 'example_data.json').as_posix()
outpath
```




    'C:/Users/camer/Projects/twitter_sentiment/data/example_data.json'




```python
# run search
twint.run.Search(c)
```

    [!] No more data! Scraping will stop now.
    found 0 deleted tweets in this search.
    

The above search took approx 3 minutes to return 22000 tweets that matched my search paramaters. For reference the json file is approx 21mb. 

The search time depends on your search paramaters and I assume somewhat on your internet connection. For 22000 tweets I don't think 3 minutes it too bad.

Note if you run this search twice, it adds to the existing JSON rather than creating a new file. There must be a setting to create a new file but I haven't found it yet.


```python

```

Posts

Here;s where i write about interesting thigns to me. Tutorials for things i've done that others might want to copy. Look at why i write link

first person

taghs

Summary Post - all code in one


TLDR:
- Twint allows you to scrape Twitter data for analysis in Python
- Vader, Textblog are open source libraries that allow you to perform sentiment analysis in Python
- From my analysis of Currys customer service twitter account @Teamknowhowuk:
  - % of tweets have negative sentiment (insert chart?)
  - Y% of the time, teakknowhow ask the compliant tweeting to dm them
  - theres x people signing off which implies how many perope responding to how many.


## Analysing the results

To view the results in a dataframe, I import the json file using pandas. Note the lines paramater needs to be set to True.


```python
# import required libraries
import pandas as pd
pd.set_option('display.max_colwidth', None)
pd.set_option('display.max_columns', None)

df =  pd.read_json('data/tweets/exampleoutput.json', lines = True)
df.shape
```

Twint returns multiple columns of data that can then be used for analysis.


```python
# view columns
df.columns
```

For example a specific tweets URL can be used to display the tweet using the requests and iptyhon libraries.


```python
# import required libraries
import requests
from IPython.display import HTML

url = 'https://publish.twitter.com/oembed?url=' + df[df['id']==1319898794830536705]['link'].values[0]
response = requests.get(url)
html = response.json()["html"]
display(HTML(html))
```

Its also easy to see who has tweeted the most, who has the most liked tweet or most retweets.


```python
# get top 10 most frequent usernames
df['username'].value_counts()[:10].sort_values(ascending=False)
```

## Searching within a Loop

I found when doing very large searches (such as searching for a whole's year of tweets for a  common keyword) often something would go wrong and the search would crash/freeze. The whole point of using Twint (over Tweepy) was to access large amounts of data and not be restricted by Twitters API limits so having it crash on large searches was not ideal.

To avoid these issues I had better results searching each day at a time in a loop and then saving individual json files that could be imported and combined into one dataframe. A special mention to Neal Caren here who took a similar approach and inspired my code.

First I create a function to do a twint search and then a function to loop over the search function for each day in a date range.


```python
# import required packages
import datetime as dt
from glob import glob
import os

def twint_search(search_term, since, until, save_path):
    c = twint.Config()
    c.Search = search_term
    c.Lang = "en"
    c.Since = since.strftime('%Y-%m-%d %H:%M:%S')
    c.Until = until.strftime('%Y-%m-%d %H:%M:%S')
    c.Hide_output = True
    c.Store_json = True
    c.Output = save_path
    twint.run.Search(c)
    
def twint_search_loop(search_term, start_date, end_date, save_dir):
    try:
        os.makedirs(os.path.join(os.getcwd(),save_dir,search_term))
        print(f'Successfully created the directory {os.path.join(os.getcwd(),save_dir,search_term)}')
    except FileExistsError:
        print(f'Directory {os.path.join(os.getcwd(),save_dir,search_term)} already exists')
    
    date_range = pd.date_range(start_date, end_date)
    
    for single_date in date_range:
        since = single_date
        until = single_date + dt.timedelta(days=1)
        save_path = os.path.join(save_dir, search_term, f'{single_date:%Y%m%d}.json')
        print(f"Searching for tweets containing '{search_term}' from {single_date:%Y-%m-%d} and saving into {save_path}")
        twint_search(search_term, since, until, save_path)
```

Let's search for every tweet containing 'teamknowhowuk' during 2020.


```python
search_term = 'teamknowhowuk'
start_date = dt.datetime(2020, 10, 1)
end_date = dt.datetime(2020, 10, 31)
save_dir = 'data/tweets'
```


```python
twint_search_loop(search_term, start_date, end_date, save_dir)
```


```python
# Retrieve paths recursively from inside the saved directory
json_files = glob(os.path.join(save_dir, search_term, '*.json'))

# Create dataframes for each json file and combine into a single df
dfs = [pd.read_json(json_file, lines = True) for json_file in json_files]
tweets_df = pd.concat(dfs).reset_index(drop=True)
tweets_df.shape
```

So same result - now have the flexibility to run for longer periods (twitter has data going back to 200X) and only import the JSON for one day and creating code before running on the full dataset.


```python
tweets_df.head()
```


```python

```

## Create new dataframe to use in sentiment analysis


```python
analysis_df = tweets_df[['id', 'created_at', 'username', 'tweet','likes_count']].copy()
analysis_df["created_at"] = pd.to_datetime(analysis_df["created_at"], utc=True)

print(analysis_df.info())
display(analysis_df.head(10))
```


```python

```

## Clean Tweets


```python
import re
def clean_tweet(tweet):
    tweet=re.sub(r"http\S+", "", tweet) #remove urls
    tweet=re.sub(r'\S+\.com\S+','',tweet) #remove urls
    tweet=re.sub(r'\@\w+','',tweet) #remove mentions
    tweet=re.sub(r'\#\w+','',tweet) #remove hashtags
    return tweet

analysis_df['cleaned_tweet']=analysis_df['tweet'].apply(lambda x: clean_tweet(x))
analysis_df.head(10)
```

## Vader Sentiment Analysis


```python
from vaderSentiment.vaderSentiment import SentimentIntensityAnalyzer
analyzer = SentimentIntensityAnalyzer()

analysis_df['vader_neg'] = analysis_df['cleaned_tweet'].apply(lambda x:analyzer.polarity_scores(x)['neg'])
analysis_df['vader_neu'] = analysis_df['cleaned_tweet'].apply(lambda x:analyzer.polarity_scores(x)['neu'])
analysis_df['vader_pos'] = analysis_df['cleaned_tweet'].apply(lambda x:analyzer.polarity_scores(x)['pos'])
analysis_df['vader_compound'] = analysis_df['cleaned_tweet'].apply(lambda x:analyzer.polarity_scores(x)['compound'])
analysis_df['vader_sentiment'] =['positive' if score > 0.05 else 'negative' if score < -0.05 else 'neutral' for score in analysis_df['vader_compound']]
```


```python
columns_to_display = ['username','cleaned_tweet', 'vader_compound', 'vader_sentiment']
analysis_df[columns_to_display].sort_values(by="vader_compound",ascending=False).head(5)
```

immediately clear daviddurbin9 tweet not picked up correctly


```python
from textblob import TextBlob
analysis_df['textblob_polarity'] = analysis_df['cleaned_tweet'].apply(lambda x: TextBlob(x).sentiment[0])
analysis_df['textblob_subjectivity'] = analysis_df['cleaned_tweet'].apply(lambda x: TextBlob(x).sentiment[1])
analysis_df['textblob_sentiment'] = ['positive' if score > 0 else 'negative' if score < 0 else 'neutral' for score in analysis_df['textblob_polarity']]

columns_to_display = ['username','cleaned_tweet', 'textblob_polarity', 'textblob_subjectivity', 'textblob_sentiment']
analysis_df[columns_to_display].sort_values(by="textblob_polarity",ascending=False).head(5)
```


```python
analysis_df['user'] = ['teamknowhowuk' if name == 'teamknowhowuk' else 'public' for name in analysis_df['username']]
analysis_df.sample(10)
```


```python
summary = analysis_df.groupby(["user"])["textblob_sentiment"].value_counts().unstack()
summary
```


```python
# add total for first chart
```


```python
summary.loc['public']
```


```python
summary['negative'].sum()
```


```python
import plotly.graph_objects as go

fig = go.Figure()

negative = go.Bar(
    #x = 'Total',
    y = summary['negative'].sum(),
    name = "Negative",
)

neutral = go.Bar(
    #x = 'Total',
    y = summary['neutral'].sum(),
    name = "neutral",
)

positive = go.Bar(
    #x = 'Total',
    y = summary['positive'].sum(),
    name = "positive",
)

layout = go.Layout(width=1000, height=600)

data = [negative, neutral, positive]

fig = go.Figure(data=data,layout=layout)
fig.update_layout(barmode='group')
fig.show()
```


```python
import plotly.graph_objects as go

fig = go.Figure()

negative = go.Bar(
    x = summary.index,
    y = summary['negative'],
    name = "Negative",
)

neutral = go.Bar(
    x = summary.index,
    y = summary['neutral'],
    name = "neutral",
)

positive = go.Bar(
    x = summary.index,
    y = summary['positive'],
    name = "positive",
)

layout = go.Layout(width=1000, height=600)

data = [negative, neutral, positive]

fig = go.Figure(data=data,layout=layout)
fig.update_layout(barmode='group')
fig.show()
```


```python
analysis_df[analysisa_df['username']!='teamknowhowuk']['textblob_sentiment'].value_counts()
analysis_df[analysis_df['username']=='teamknowhowuk']['textblob_sentiment'].value_counts()
```


```python
summary_df = pd.pivot_table(analysis_df, index=['user'])
                            #values='textblob_sentiment', index=['user'], columns=['textblob_sentiment'], aggfunc='count')
summary_df
#analysis_df.groupby(['user','textblob_sentiment'])['textblob_sentiment'].count()
#display(summary_df)
```


```python
import plotly.graph_objects as go

fig = go.Figure(
    [go.Bar(
        x=analysis_df[analysis_df['username']!='teamknowhowuk']['textblob_sentiment'].value_counts().index,
        y=analysis_df[analysis_df['username']!='teamknowhowuk']['textblob_sentiment'].value_counts(),
    )]
)
fig.show()
```


```python

```

#### import plotly.graph_objects as go

data = go.Histogram(x=analysis_df['textblob_polarity'],nbinsx=21)
layout = go.Layout(width=1000, height=600)

fig = go.Figure(data=data,layout=layout)

fig.show()



```python

public = go.Histogram(x=analysis_df[analysis_df['username']!='teamknowhowuk']['textblob_polarity'],nbinsx=20,name='public')
teamknowhowuk = go.Histogram(x=analysis_df[analysis_df['username']=='teamknowhowuk']['textblob_polarity'],nbinsx=20, name='teamknowhow')
layout = go.Layout(width=1000, height=600)

data = [public, teamknowhowuk]
fig = go.Figure(data=data,layout=layout)
fig.update_layout(barmode='overlay')
fig.update_traces(opacity=0.75)
fig.show()
```


```python
import plotly.graph_objects as go
import textwrap

teamknowhowuk = go.Scatter(
    x=analysis_df[analysis_df['username']=='teamknowhowuk']['textblob_polarity'], 
    y=analysis_df[analysis_df['username']=='teamknowhowuk']['textblob_subjectivity'],
    mode='markers', name='teamknowhowuk', marker_color='fuchsia', opacity=0.5,
    hoverinfo="text", hovertext = analysis_df[analysis_df['username']=='teamknowhowuk']['tweet'].apply(lambda txt: '<br>'.join(textwrap.wrap(txt, width=50))),
)

public = go.Scatter(
    x=analysis_df[analysis_df['username']!='teamknowhowuk']['textblob_polarity'], 
    y=analysis_df[analysis_df['username']!='teamknowhowuk']['textblob_subjectivity'],
    mode='markers', name='public', marker_color='turquoise', opacity=0.75,
    hoverinfo="text", hovertext = analysis_df[analysis_df['username']!='teamknowhowuk']['tweet'].apply(lambda txt: '<br>'.join(textwrap.wrap(txt, width=50))),
)

layout = go.Layout(
    title='Textblob Sentiment Analysis',
    width=1000, height=600,
    template='seaborn',
    xaxis_title='<--- Negative Sentiment                 Positive Sentiment --->',
    yaxis_title='<--- Objective / Facts               Subjective / Opinions --->',
    hoverlabel_align = 'right',
    legend = {'yanchor': 'bottom', 'y': 1, 'xanchor': 'right', 'x': 1, 'orientation': 'h'},
    margin=dict(l=60, r=60, b=60, t=75),
    xaxis_range= [-1.025,1.025], yaxis_range= [-0.025,1.025]
)

data = [teamknowhowuk, public]

fig = go.Figure(data=data, layout=layout)
#fig.show()
```


```python

textwrap.shorten("Hello  world!", width=11)
```


```python

```


```python

afinn = Afinn() #afinn = Afinn(emoticons=True)
analysis_df['afinn_score'] = analysis_df['tweet'].apply(afinn.score)
```


```python

```


```python
analysis_df.sort_values(by="vader_compound",ascending=False).head(5)
```


```python

```


```python

```


```python

```


```python
analysis_df[columns_to_display].sort_values(by="vader_compound",ascending=True).head(5)
```


```python
analysis_df[analysis_df['username']=='teamknowhowuk'][columns_to_display].sort_values(by="vader_compound",ascending=True).head(5)
```


```python

```


```python

```


```python
from textblob import TextBlob
```


```python
analysis_df[analysis_df.duplicated(['tweet'])].drop_duplicates(subset=['tweet'])
```


```python
# Five user who got most frequent like
analysis_df.sort_values(by="likes_count",ascending=False).head(5)
```


```python

```


```python

```


```python

```


```python
analysis_df['vader_compound'].describe()
```


```python
analysis_df[columns_to_display].groupby(['username']).sum().sort_values(by="vader_compound",ascending=False).head(10)
```


```python
analysis_df[analysis_df['username']=='joyfulbrand']
```


```python

```


```python

```


```python

```


```python
import plotly.graph_objects as go

data = go.Histogram(x=analysis_df['vader_compound'],nbinsx=20)
layout = go.Layout(width=1000, height=600)
fig = go.Figure(data=data,layout=layout)

fig.show()

public = go.Histogram(x=analysis_df[analysis_df['username']!='teamknowhowuk']['vader_compound'],nbinsx=20,name='public')
teamknowhowuk = go.Histogram(x=analysis_df[analysis_df['username']=='teamknowhowuk']['vader_compound'],nbinsx=20, name='teamknowhow')
layout = go.Layout(width=1000, height=600)

data = [public, teamknowhowuk]
fig = go.Figure(data=data,layout=layout)
fig.update_layout(barmode='overlay')
fig.update_traces(opacity=0.75)
fig.show()
```


```python
public = go.Histogram(x=analysis_df[analysis_df['username']!='teamknowhowuk']['vader_compound'],nbinsx=20,name='public')
teamknowhowuk = go.Histogram(x=analysis_df[analysis_df['username']=='teamknowhowuk']['vader_compound'],nbinsx=20, name='teamknowhow')
layout = go.Layout(width=1000, height=600)

data = [public, teamknowhowuk]
fig = go.Figure(data=data,layout=layout)
fig.update_layout(barmode='overlay')
fig.update_traces(opacity=0.75)
fig.show()
```


```python
# Create a document
all_words = ' '.join([tweet for tweet in analysis_df['cleaned_tweet']])
# Create a WordCloud object
wordCloud = WordCloud(background_color='black', 
                      width=800, height=300,
                      random_state=21, max_font_size=110,
                      max_words=200, 
                      contour_color='black', 
                      contour_width=1).generate(all_words)
# Plot WordCloud object
plt.figure(figsize=[8,8])
plt.imshow(wordCloud, interpolation="bilinear")
plt.axis('off')
plt.show()
```


```python
TextBlob('this is a test message i really like but find terrible to use').sentiment
```


```python
analyzer.polarity_scores('this is a test message i really like but find terrible to use')
```


```python

```


```python
analysis_df['textblob_polarity'] = analysis_df['tweet'].apply(textblob_sentiment).apply(lambda x: x[0])
analysis_df['textblob_subjectivity'] = analysis_df['tweet'].apply(textblob_sentiment).apply(lambda x: x[1])
analysis_df['textblob_sentiment'] = ['positive' if score > 0 else 'negative' if score < 0 else 'neutral' for score in analysis_df['textblob_polarity']]


afinn = Afinn() #afinn = Afinn(emoticons=True)
analysis_df['afinn_score'] = analysis_df['tweet'].apply(afinn.score)

```


```python
Now i looked at sentiment - vader vs texblog.
```


```python

```


```python
test = TextBlob('love  service')
print(test.sentiment)
```

https://textblob.readthedocs.io/en/dev/quickstart.html

The sentiment property returns a namedtuple of the form Sentiment(polarity, subjectivity). 

The polarity score is a float within the range [-1.0, 1.0]. 

The subjectivity is a float within the range [0.0, 1.0] where 0.0 is very objective and 1.0 is very subjective.


```python

```


```python

```


```python
from textblob import TextBlob
def textblob_sentiment(text):
    try:
        return TextBlob(text).sentiment
    except:
        return None
    
analysis_df['textblob_polarity'] = analysis_df['tweet'].apply(textblob_sentiment).apply(lambda x: x[0])
analysis_df['textblob_subjectivity'] = analysis_df['tweet'].apply(textblob_sentiment).apply(lambda x: x[1])
analysis_df['textblob_sentiment'] = ['positive' if score > 0 else 'negative' if score < 0 else 'neutral' for score in analysis_df['textblob_polarity']]
analysis_df.sample(10)
```


```python

```


```python
analysis_df['textblob_sentiment'].value_counts()
```


```python
analysis_df[analysis_df['username']=='teamknowhowuk']['textblob_sentiment'].value_counts()
```


```python
analysis_df[analysis_df['username']!='teamknowhowuk']['textblob_sentiment'].value_counts()
```


```python
from vaderSentiment.vaderSentiment import SentimentIntensityAnalyzer
analyzer = SentimentIntensityAnalyzer()
```


```python
analysis_df['vader_neg'] = analysis_df['tweet'].apply(lambda x:analyzer.polarity_scores(x)['neg'])
analysis_df['vader_neu'] = analysis_df['tweet'].apply(lambda x:analyzer.polarity_scores(x)['neu'])
analysis_df['vader_pos'] = analysis_df['tweet'].apply(lambda x:analyzer.polarity_scores(x)['pos'])
analysis_df['vader_compound'] = analysis_df['tweet'].apply(lambda x:analyzer.polarity_scores(x)['compound'])
analysis_df['vader_sentiment'] =['positive' if score > 0.05 else 'negative' if score < -0.05 else 'neutral' for score in analysis_df['vader_compound']]
```


```python
analysis_df['vader_sentiment'].value_counts()
```


```python
analysis_df[analysis_df['username']=='teamknowhowuk']['vader_sentiment'].value_counts()
```


```python
analysis_df[analysis_df['username']!='teamknowhowuk']['vader_sentiment'].value_counts()
```


```python
#pip install afinn
#https://github.com/fnielsen/afinn
from afinn import Afinn
afinn = Afinn() #afinn = Afinn(emoticons=True)
analysis_df['afinn_score'] = analysis_df['tweet'].apply(afinn.score)
```


```python
analysis_df['afinn_score'] = analysis_df['tweet'].apply(afinn.score)
```


```python
analysis_df[analysis_df['username']=='teamknowhowuk'].sort_values(by='afinn_score')[columns_to_display].head(10)
```


```python
columns_to_display = ['tweet', 'afinn_score']
analysis_df.sort_values(by='afinn_score')[columns_to_display].tail(10)
#analysis_df.sort_values(by='afinn_score').head(10)
```


```python
analysis_df[(analysis_df['textblob_sentiment'] == 'positive')&(analysis_df['vader_sentiment'] == 'negative')]
```


```python
analysis_df[(analysis_df['textblob_sentiment']=='positive') & (analysis_df['vader_sentiment']=='positive') & ~(analysis_df['username']=='teamknowhowuk')]
```


```python
analysis_df['vader_compound'].idxmax()
```


```python
analysis_df.groupby('vader_sentiment').count().reset_index()
```


```python
fig = go.Figure()

fig.add_trace(go.Bar(
    x = ['Negative', 'Neutral', 'Positive'],
    y = [8, 12, 4],
    color = ['red','blue','green']
    name = "Textblob",
))

#fig.add_trace(go.Bar(
#    x = ['Negative', 'Neutral', 'Positive'],
#    y = [5, 10, 5],
#    name = "Vader",
#))

fig.update_layout(title_text="Multi-category axis")

fig.show()
```


```python
import plotly.graph_objects as go

fig = go.Figure()

fig.add_trace(go.Bar(
  x = [['Vader', 'Vader', 'Textblob', 'Textblob'],
       ["A", "A", "A", "A"]],
  y = [2, 3, 1, 5],
  name = "Neutral",
))

fig.add_trace(go.Bar(
  x = [['Vader', 'Vader', 'Textblob', 'Textblob'],
       ["A", "A", "A", "A"]],
  y = [8, 3, 6, 5],
  name = "Negative",
))

fig.add_trace(go.Bar(
  x = [['Vader', 'Vader', 'Textblob', 'Textblob'],
       ["A", "A", "A", "A"]],
  y = [8, 3, 6, 5],
  name = "Positive",
))

fig.update_layout(title_text="Multi-category axis")

fig.show()
```


```python
fig = go.Figure()
fig.add_trace(go.Histogram(x=analysis_df['vader_sentiment']))
fig.add_trace(go.Histogram(x=analysis_df['textblob_sentiment']))
#fig.add_trace(go.Histogram(x="textblob_sentiment"))
fig.update_xaxes(categoryorder='array', categoryarray= ['negative','neutral','positive'])
# Overlay both histograms
#fig.update_layout(barmode='overlay')
# Reduce opacity to see both histograms
fig.update_traces(opacity=0.75)
fig.show()


```


```python
import plotly.express as px

fig = px.histogram(analysis_df, x="vader_sentiment")
fig.show()
```


```python
manually validate scores - vader handles text better as does emoticons? https://stackoverflow.com/questions/47760662/sentiment-analysis-in-python-textblob-vs-vader
```


```python

```


```python
analyzer.polarity_scores(analysis_df['tweet'].iloc[0])
```


```python
analysis_df['tweet'].iloc[0]
```


```python
analyzer.polarity_scores('so how long exactly do I have to wait to find out where the printer I ordered 3 weeks ago has gone? No printer, no refund, no communication')
```


```python
analysis_df['textblob_polarity'] = analysis_df['tweet'].apply(textblob_sentiment).apply(lambda x: x[0])
analysis_df['textblob_subjectivity'] = analysis_df['tweet'].apply(textblob_sentiment).apply(lambda x: x[1])
analysis_df['textblob_sentiment'] = ['positive' if score > 0 else 'negative' if score < 0 else 'neutral' for score in analysis_df['textblob_polarity']]
analysis_df.sample(10)
```


```python

```


```python
need to reindex?
```


```python

#textblob_sentiment = ['positive' if score > 0 else 'negative' if score < 0 else 'neutral' for score in analysis_df['textblob_polarity']]
#textblob_sentiment
analysis_df.sample(10)
```


```python
import plotly.graph_objects as go

import numpy as np

fig = go.Figure(data=[go.Histogram(x=analysis_df['textblob_polarity'])])

fig.show()
```


```python
import plotly.graph_objects as go

import numpy as np

x0 = np.random.randn(500)
# Add 1 to shift the mean of the Gaussian distribution
x1 = np.random.randn(500) + 1

fig = go.Figure()
fig.add_trace(go.Histogram(x=x0))
fig.add_trace(go.Histogram(x=x1))

# Overlay both histograms
fig.update_layout(barmode='overlay')
# Reduce opacity to see both histograms
fig.update_traces(opacity=0.75)
fig.show()
```


```python

```


```python
df['Polarity]     = df[TEXT].apply(sentiment).apply(lambda x: x[0])
df['Subjectivity] = df[TEXT].apply(sentiment).apply(lambda x: x[1])
```


```python
def get_polarity(text):
    return TextBlob(text).sentiment.polarity

analysis_df['Polarity'] = analysis_df['tweet'].apply(get_polarity)

analysis_df['Sentiment']='NEUTRAL'
analysis_df.loc[analysis_df.Polarity>0.25,'Sentiment']='POSITIVE'
analysis_df.loc[analysis_df.Polarity<-0.25,'Sentiment']='NEGATIVE'

analysis_df.sample(5)
```


```python
analysis_df[analysis_df['username']=='teamknowhowuk']['Sentiment'].value_counts().plot(kind='bar',title="Sentiment Analysis")
```


```python
analysis_df[analysis_df['username']!='teamknowhowuk']['Sentiment'].value_counts().plot(kind='bar',title="Sentiment Analysis")
```


```python
analysis_df[analysis_df['username']!='teamknowhowuk']
```


```python
from textblob import TextBlob
df2['textblog_sent'] = df['tweet'].apply(lambda tweet: TextBlob(tweet).sentiment)
df2.head()
```


```python

```


```python
import nltk
nltk.download('vader_lexicon')
from nltk.sentiment.vader import SentimentIntensityAnalyzer
sid = SentimentIntensityAnalyzer()
```


```python

def get_polarity(text):
    return TextBlob(text).sentiment.polarity

analysis_df['scores'] = analysis_df['tweet'].apply(lambda tweet: sid.polarity_scores(tweet))

analysis_df['compound']  = analysis_df['scores'].apply(lambda score_dict: score_dict['compound'])

analysis_df['vader_sentiment_type']='NEUTRAL'
analysis_df.loc[analysis_df.compound>0.25,'vader_sentiment_type']='POSITIVE'
analysis_df.loc[analysis_df.compound<-0.25,'vader_sentiment_type']='NEGATIVE'

analysis_df.sample(5)


```


```python
analysis_df[analysis_df['username']!='teamknowhowuk']['vader_sentiment_type'].value_counts().plot(kind='bar',title="Sentiment Analysis")
```


```python
analysis_df[analysis_df['username']=='teamknowhowuk']['vader_sentiment_type'].value_counts().plot(kind='bar',title="Sentiment Analysis")
```


```python
%%time
# Create a function to get the subjectivity
def getSubjectivity(text):
   return TextBlob(text).sentiment.subjectivity

# Create a function to get the polarity
def getPolarity(text):
   return  TextBlob(text).sentiment.polarity
 

# Create two new columns 'Subjectivity' & 'Polarity'
df2['Subjectivity'] = df2['tweet'].apply(getSubjectivity)
df2['Polarity'] = df2['tweet'].apply(getPolarity)

df2.head()
```


```python
from vaderSentiment.vaderSentiment import SentimentIntensityAnalyzer
analyzer = SentimentIntensityAnalyzer()

scores = []
# Declare variables for scores
compound_list = []
positive_list = []
negative_list = []
neutral_list = []
for i in range(df2['tweet'].shape[0]):
#print(analyser.polarity_scores(sentiments_pd['text'][i]))
    compound = analyzer.polarity_scores(df2['tweet'][i])["compound"]
    pos = analyzer.polarity_scores(df2['tweet'][i])["pos"]
    neu = analyzer.polarity_scores(df2['tweet'][i])["neu"]
    neg = analyzer.polarity_scores(df2['tweet'][i])["neg"]
    
    scores.append({"Compound": compound,
                   "Positive": pos,
                   "Negative": neg,
                   "Neutral": neu
                  })
```


```python
df2.head()
```


```python

```


```python

```


```python

```


```python
# check to see whats best for own tweets.
df2[df2['username']=='cammclean182']
```

References:
-https://nealcaren.org/lessons/twint/


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

import datetime as dt
from glob import glob
import os

%%time
```


```python

```


```python

```


```python

```


```python
df[df['username']=='teamknowhowuk']

- get last name
- plot time of each person replying
```


```python

```


```python

```


```python

```


```python
### Summary code in one block
```
