import pandas as pd
from bs4 import BeautifulSoup
from urllib.request import urlopen

page = 'https://whichmuseum.nl/nederland/beste-musea'
raw_html = urlopen(page)
soup = BeautifulSoup(raw_html, 'html.parser')

musea_raw = soup.findAll('div', class_="small-12 medium-12 large-12 columns listview medium")

output_list = []
for museum in musea_raw:
    item = {'Rank':museum.find('div', class_='rank').text,
            'Name':museum.find('h3').text.strip('\n ').strip(museum.find('span', class_='city').text),
            'City':museum.find('span', class_='city').text,
            'Description':museum.find('h4').text}
    output_list.append(item)
    
musea_df = pd.DataFrame(output_list)
