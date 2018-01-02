Note: I didn't get the cvs, after I activated the virtual environment I wrote all this code in the command prompt 
to do this just write:

## python 

after activating virtual environment.

Note: I'm using python 2.7.14

## ok, let's get to business!

 1) go to your cmd, and type in:
easy_install pip  
pip install BeautifulSoup4

Be sure to activate virtual environment.

2.) In notepad++ make sure you're in python mode and write the code below:

# importing libraries
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

#Import Twilio (pip install twilio)
from twilio.rest import Client

account_sid = 'xxx'
auth_token = 'xxx'

client = Client(account_sid, auth_token)

#Text the information via Twilio
body = title + ', ' + priceblock_ourprice
message = client.messages.create(
   	to="+your phone number",
    from_="twilio phone number",
    body=body)
