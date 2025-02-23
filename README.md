# yhangry-chef-scraper
Assessment
import requests
from bs4 import BeautifulSoup

URL = 'https://www.linkedin.com/jobs/search/?keywords=chef'
headers = {'User-Agent': 'Mozilla/5.0'}
response = requests.get(URL, headers=headers)
soup = BeautifulSoup(response.text, 'html.parser')

jobs = soup.find_all('div', class_='result-card')
for job in jobs:
    title = job.find('h3', class_='result-card__title').text.strip()
    company = job.find('h4', class_='result-card__subtitle').text.strip()
    print(f"Job: {title}, Company: {company}")
