# scrapy
Scrapy tutorial

#Step 1  Install anaconda

#Step 2 Run the following command In the Anaconda terminal: conda install -c conda-forge scrapy

#Step 3 Open Anaconda.navigator and open Spyder or Visual studio (it doesn't really matter but you should use spyde if you're planning on using scrapy)

#Step 4 Create a .py file where you will paste in your scraper code and safe it as (You can change the name example) : example_spider.py

#Step 5 Build your code or use this example and safe it in your example_spider.py file 
#substep for step 5   paste this code (if you are new to using scrapy) (it's better to first get this to work before you focus on writing your own scraper) :)

import scrapy


class QuotesSpider(scrapy.Spider):
    name = "quotes"
    start_urls = [
        'http://quotes.toscrape.com/page/1/',
        'http://quotes.toscrape.com/page/2/',
    ]

    def parse(self, response):
        for quote in response.css('div.quote'):
            yield {
                'text': quote.css('span.text::text').get(),
                'author': quote.css('small.author::text').get(),
                'tags': quote.css('div.tags a.tag::text').getall(),
            }


#Step 6  Run the following command in your anaconda terminal:   scrapy runspider example_spider.py -O items.json
(this will write the output of your scraper into a items.json file)

#Step 7 Check if the command was succesful
(The output should be the following):

[
{"text": "\u201cThe world as we have created it is a process of our thinking. It cannot be changed without changing our thinking.\u201d", "author": "Albert Einstein"},
{"text": "\u201cIt is our choices, Harry, that show what we truly are, far more than our abilities.\u201d", "author": "J.K. Rowling"},
{"text": "\u201cThere are only two ways to live your life. One is as though nothing is a miracle. The other is as though everything is a miracle.\u201d", "author": "Albert Einstein"},
{"text": "\u201cThe person, be it gentleman or lady, who has not pleasure in a good novel, must be intolerably stupid.\u201d", "author": "Jane Austen"},
{"text": "\u201cImperfection is beauty, madness is genius and it's better to be absolutely ridiculous than absolutely boring.\u201d", "author": "Marilyn Monroe"},
{"text": "\u201cTry not to become a man of success. Rather become a man of value.\u201d", "author": "Albert Einstein"},
{"text": "\u201cIt is better to be hated for what you are than to be loved for what you are not.\u201d", "author": "Andr\u00e9 Gide"},
{"text": "\u201cI have not failed. I've just found 10,000 ways that won't work.\u201d", "author": "Thomas A. Edison"},
{"text": "\u201cA woman is like a tea bag; you never know how strong it is until it's in hot water.\u201d", "author": "Eleanor Roosevelt"},
{"text": "\u201cA day without sunshine is like, you know, night.\u201d", "author": "Steve Martin"}
]

#Step 8 Delete the items.json file and change the code and see for yourself if you can change the output



Hope this helped :)

Made by Milan :)
