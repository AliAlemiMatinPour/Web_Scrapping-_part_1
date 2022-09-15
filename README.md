# Web_Scrapping-_part_1
I'm doing web Scraping of the IDM website for the top best watch. I am using Jupyter Notebook, and python libs such as beautiful soup, requests, and openpyxl. I am mining data from the front end HTML file and converting them into xlsx file.

# BeautifulSoup
<img width="1000" align='center' src="https://raw.githubusercontent.com/harryworlds/harryworlds/main/mech_can_code.png">

#I'm using Beautiful soup and rest are simple coding and you can test this code through replit.com an online IDE.

[![Website](https://img.shields.io/website?label=click_here_to_test_code_Python&style=for-the-badge&url=https://replit.com/@harryworlds/WebScrappingpart1?v=1)](https://replit.com/@harryworlds/WebScrappingpart1?v=1)

[![Website](https://img.shields.io/website?label=Click_here/harryworls_Github&style=for-the-badge&url=https://github.com/harryworlds)](https://github.com/harryworlds)




---
</br>

<img width="1200" align='center' src="https://github.com/harryworlds/Web_Scrapping-_part_1/blob/main/web_Scrapping%20_harryworlds_part_1.png">

---
<br/>
<img width="1200" align='center' src="https://raw.githubusercontent.com/harryworlds/Web_Scrapping-_part_1/main/replit.png">

<img width="100" align='left' src="https://emojipedia-us.s3.amazonaws.com/source/microsoft-teams/337/beaming-face-with-smiling-eyes_1f601.png"> 

# <> CODE IS HERE <>

<!--START_SECTION:waka-->
```text
import pandas as pd 
from bs4 import BeautifulSoup
import requests, openpyxl 

excel = openpyxl.Workbook() 
print(excel.sheetnames)

sheet = excel.active
sheet.title = "Top Movies to watch"
print(excel.sheetnames)
sheet.append(['Rank','Movie Title', 'Year of Release', 'Rating']) #Meta data or heading of spread sheet

try: #block lets you test a block of code for errors
    page = requests.get("https://www.imdb.com/chart/top/") #link for page to collect data
    # page.raise_for_status() # capture an error

    lentil_soup = BeautifulSoup(page.text,"html.parser") #data stored and type of format
    harry_movie_Search = lentil_soup.find('tbody', class_="lister-list").find_all('tr') #access to movies data
    
    for movie in harry_movie_Search:
        serial_number = movie.find('td', class_="titleColumn").get_text(strip=True).split(".")[0] 
        name_of_movie = movie.find('td', class_="titleColumn").a.text
        year_of_release = movie.find('td', class_="titleColumn").span.text.strip("()")
        movie_rating = movie.find('td', class_="ratingColumn imdbRating").strong.text

        print(serial_number, name_of_movie, year_of_release, movie_rating)
        sheet.append([serial_number, name_of_movie, year_of_release, movie_rating])
        # break ##break command is for single inspection (which break loop
except Exception as harry_world: #lets you handle the error
    print(harry_world)

excel.save('IMDB Best Movie Rating.xlsx')


```
<!--END_SECTION:waka-->
---
Thansk for reading and hopefully, you enjyoed it.

[![Website](https://img.shields.io/website?label=Click_here/harryworls_Github&style=for-the-badge&url=https://github.com/harryworlds)](https://github.com/harryworlds)

