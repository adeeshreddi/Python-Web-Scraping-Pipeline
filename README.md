# Python-Web-Scraping-Pipeline
A Python-based web scraping pipeline for extracting and structuring Toyota car listing data from AckoDrive using Requests, BeautifulSoup, and Pandas.
# Python Web Scraping Pipeline

This project is a complete web scraping pipeline built using Python, Requests, BeautifulSoup, and Pandas. It focuses on extracting car listings from the AckoDrive website and converting them into a structured dataset for analysis and further processing.

The pipeline demonstrates how to fetch a webpage, parse HTML, extract useful information, clean data, and store it in a CSV file.

---

## 🚗 Project Overview

The goal of this project is to learn and implement:

- How to scrape real-world websites  
- How to navigate HTML tags (div, p, a)  
- How to extract specific fields from structured web content  
- How to clean and format data using Python  
- How to store results in CSV for analysis  

This pipeline currently extracts the following details:

- *Model name*  
- *Price*  
- *Fuel type*  
- *Transmission type*  
- *Location (Mumbai)*  

---

## 🛠 Technologies & Tools

- *Python 3*
- *Requests* – Fetch HTML pages  
- *BeautifulSoup (bs4)* – Parse and extract data  
- *Pandas* – Create and clean DataFrames  
- *Regex* – Text extraction & cleaning  

---

## 📁 Files Included

- web_scraping_pipeline.ipynb — Main notebook with the entire pipeline  
- acko_toyota_mumbai.csv — Final dataset generated from scraping  

---

## 🔍 How the Pipeline Works

1. *HTTP Request*  
   The script fetches the AckoDrive Toyota cars page using requests.get().

2. *HTML Parsing*  
   BeautifulSoup reads the HTML and converts it into a searchable structure.

3. *Card Identification*  
   The scraper identifies the main grid of car listings and finds each car card.

4. *Data Extraction*  
   From each car card, the pipeline extracts:
   - Model name  
   - Price  
   - Fuel type  
   - Transmission  

5. *Data Structuring*  
   Extracted details are stored in a list of dictionaries.

6. *DataFrame Creation*  
   Pandas converts the list into a structured table.

7. *CSV Export*  
   The final DataFrame is saved as acko_toyota_mumbai.csv.

---

## 📌 Sample Code Snippet

```python
response = requests.get(url)
soup = BeautifulSoup(response.text, "html.parser")

cards_grid = soup.find('div', class_='CarBrowsingSection_cardsGrid__lVvIX')
car_cards = cards_grid.find_all('div', class_='BuyCarCard_card__AsGXF')

for card in car_cards:
    model = card.find('a', class_='BuyCarCard_carName__SAJVh').get_text(strip=True)
    price = card.find('p', class_='BuyCarCard_priceRange__2q8tm').get_text(strip=True)
