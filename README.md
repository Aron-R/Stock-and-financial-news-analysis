# Sentiment analysis of Stock market and financial news articles

fetches all the urls and scrapes data from the news archives of  
  * thehindu.com.
  * ndtv.com
  * thehindubusinessline.com
  * economictimes.indiatimes.com
  * reuters.com
  * moneycontrol.com
  
## Setting up
Download  chrome driver from  [link](http://chromedriver.chromium.org/downloads).

Unzip it and then place the chromedriver in the root directory.

To setup the dependencies,
```
pip install -r requirements.txt.
```
## Note

It is currently incomplete as the goal is to webscrape and analyse any article from any website
But to get started, i'm using this code.

## Usage

Currently the pipeline is available till merging step. **Scrapy and sentiment integration are to be done.**
The complete help to use the following repo is as follows:
```
usage: parser.py [-h] -s START -e END -w [WEB] [-r REGEXP]

Runs the entire pipeline from scraping to extracting sentiments.

optional arguments:
  -h, --help            show this help message and exit
  -s START, --start START
                        Start date,format-(dd/mm/yy)
  -e END, --end END     End date,format-(dd/mm/yy)
  -w [WEB], --web [WEB]
                        Specify the website number to scrape from separated by space						
                        0=economictimes.indiatimes.com						
                        1=reuters.com						
                        2=ndtv.com						
                        3=thehindubusinessline.com						
                        4=moneycontrol.com						
                        5=thehindu.com
                        
  -r REGEXP, --regexp REGEXP
                        Complete path to the regex list file for companies. 
                        For template refer regesList file at root directory of this repo.
                        By default, it runs the regexList file present at root directory of this repo.
```
A sample run from **20/03/2012** to **19/08/2014** for 
* economictimes

would be given as follows:
```
python parser.py -s 20/03/2012 -e 19/08/2014 -w 0 
```

## File Description 

      -> regexList- Contains the regex for the company name to enhance search results and get more relevant results.
      -> search_scrape.py- Scrapes urls from the google search results.
      -> filter.py- Filters the relevant urls collected from google search results.
      -> archive_scraper.py - Scrapes urls from archives of various websites.
      -> scrape_with_bs4.py- Scrapes the content from the scraped urls.
      -> quick_scraper.py- Scrapes content parallely and faster by sending multiple requests per second.
      -> merger.py- Merges the data collected from google search results and news archive.
      -> sentiment.py - Calculates the sentiment of the collected data.
