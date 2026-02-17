# Task-3
web scraper for news headlines
import requests
from bs4 import BeautifulSoup

# Step 1: Website URL
url = "https://www.bbc.com/news"

# Step 2: Send request
response = requests.get(url)

# Step 3: Convert to text (HTML)
html = response.text

# Step 4: Parse HTML
soup = BeautifulSoup(html, "html.parser")

# Step 5: Find all h2 tags (headlines)
headlines = soup.find_all("h2")

# Step 6: Print headlines
print("Top News Headlines:\n")

for headline in headlines:
    text = headline.get_text().strip()
    if text != "":
        print("-", text)
        with open("headlines.txt", "w", encoding="utf-8") as file:
    for headline in headlines:
        text = headline.get_text().strip()
        if text != "":
            file.write(text + "\n")

print("\nHeadlines saved to headlines.txt")
