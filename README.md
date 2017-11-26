# scraping
# import libraries
import urllib2
from bs4 import BeautifulSoup

quote_page = 'https://www.amazon.com/Jimmy-Paddox-Leather-Black-Biker/dp/B0771TB2Y1/ref=sr_1_9?s=apparel&ie=UTF8&qid=1511230028&sr=1-9&nodeID=7141123011&psd=1'

page = urllib2.urlopen(quote_page)

soup = BeautifulSoup(page, 'html.parser')

title_box = soup.find('h1', attrs={'id': 'title'}) 

title = title_box.text.strip()

print title

priceblock_ourprice_box = soup.find('span', attrs={'id':'priceblock_ourprice'})

priceblock_ourprice = priceblock_ourprice_box.text

print priceblock_ourprice

