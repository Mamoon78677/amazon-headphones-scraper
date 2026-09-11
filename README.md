# Amazon Headphones Scraper 🎧

A production-ready, lightweight Python web scraper designed to extract product data from Amazon search result pages. This project was built completely from scratch using core Python and standard developer tools to master the mechanics of HTML inspection, master container looping, and robust data extraction.

## 🚀 Features
* **Master Container Trapping:** Targets the master `puis-card-container` to isolate product cards and prevent descriptive data mix-ups.
* **Resilient Extraction:** Uses secure text-extraction logic to gracefully fall back to `N/A` instead of crashing on empty fields.
* **Anti-Bot Countermeasures:** Dynamically randomizes `User-Agent` headers using `fake_useragent` to mimic legitimate user actions.
* **Automated Pipeline:** Parses raw HTML directly into a clean, formatted `.csv` file containing product names, prices, and star ratings.

## 🛠️ Tech Stack
* **Language:** Python 3.x
* **Libraries:** `requests`, `BeautifulSoup` (bs4), `fake_useragent`, `csv`

## 📦 Installation & Setup

To run this project on your local machine, you need to install the external Python libraries used in the script. Open your terminal or command prompt and run the following commands:

```bash
# 1. Clone this repository
git clone https://github.com
cd amazon-headphones-scraper

# 2. Install the required web scraping packages
pip install requests beautifulsoup4 fake-useragent
```

*(Note: If you are using a Jupyter Notebook, run `!pip install requests beautifulsoup4 fake-useragent` inside a cell to prepare your environment).*

## ⚙️ How It Works

### 1. Trapping the Outer Wrapper
Instead of parsing localized text fragments directly, the script segments the document into complete independent product cards:
```python
headphones = soup.find_all("div", class_="puis-card-container")
```

### 2. Sifting Inside the Cards
Once a master card is isolated, the scraper executes an internal localized search to match fields precisely:
```python
title = headphone.find("h2")
price = headphone.find("span", class_="a-price-whole")
rating = headphone.find("i", class_="a-icon")
```

## 📊 Sample Output File (`headphones.csv`)

| Index | Title | Price | Rating |
| :--- | :--- | :--- | :--- |
| 1 | Hybrid Active Noise Cancelling Bluetooth Headphones Wireless Headphones... | 8,591. | 4.3 out of 5 stars |
| 4 | BERIBES Bluetooth Headphones Over Ear Wireless HiFi Stereo Headsets... | 5,530. | 4.5 out of 5 stars |
| 5 | Raycon The Everyday Wireless Bluetooth Over Ear Headphones, with Active... | 26,333. | 4.5 out of 5 stars |

---
*Disclaimer: This repository was created for educational purposes to study web parsing structures and developer tools workflow pipelines.*
