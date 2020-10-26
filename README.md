Note: I didn't get the cvs, after I activated the virtual environment I wrote all this code in the command prompt 
to do this just write:

## python 

after activating virtual environment.

Note: I'm using python 2.7.14

## ok, let's get down to business!

 1) go to your cmd, and type in:
easy_install pip  
pip install BeautifulSoup4

Be sure to activate virtual environment.

2.) In notepad++ make sure you're in python mode and write the code below:

# importing libraries
import urllib2  <--------- (start here)

from bs4 import BeautifulSoup

quote_page = 'https://www.amazon.com/Jimmy-Paddox-Leather-Black-Biker/dp/B0771TB2Y1/ref=sr_1_9?s=apparel&ie=UTF8&qid=1511230028&sr=1-9&nodeID=7141123011&psd=1' <----- click the link, and get the link from the official website. DO NOT USE THIS ONE EVEN THOUGH IT'S THE SAME,or you'll get an error in your cmd.

page = urllib2.urlopen(quote_page)

soup = BeautifulSoup(page, 'html.parser')

title_box = soup.find('h1', attrs={'id': 'title'}) 

title = title_box.text.strip()

print title

priceblock_ourprice_box = soup.find('span', attrs={'id':'priceblock_ourprice'})

priceblock_ourprice = priceblock_ourprice_box.text

print priceblock_ourprice


