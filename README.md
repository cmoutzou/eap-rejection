# eap-rejection
Dynamic Web Scraping App using Python Selenium
This project automates the process of web scraping a government website where payroll files are uploaded. The primary goal is to extract records of payroll transactions that could not be paid successfully and export the data into a CSV file. The code is designed to handle dynamic web pages where elements (buttons, links) change daily. This project is intended to run on Google Colab.

Features
Connects to a government web page and logs in with provided credentials.
Navigates through the site, dynamically clicking buttons and links.
Scrapes data from dynamically changing tables.
Exports scraped data into an Excel file with specific formatting.
Utilizes Selenium for web automation and XlsxWriter for Excel file creation.
Installation
To run this project, you'll need to install the following Python packages:


!pip install selenium
!pip install chromedriver-autoinstaller
!pip install XlsxWriter
Usage
Setup and Initialization
Clone the repository:


git clone https://github.com/yourusername/your-repo-name.git
cd your-repo-name
Open the script in Google Colab:

Upload the script to Google Colab or copy the content into a new Colab notebook.

Install dependencies in Colab:


!pip install selenium
!pip install chromedriver-autoinstaller
!pip install XlsxWriter
Import necessary modules:

import pandas as pd
import sys
import time
import xlsxwriter
from bs4 import BeautifulSoup
from selenium import webdriver
import chromedriver_autoinstaller
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from selenium.webdriver.common.by import By
from google.colab import drive, files
Script Execution
Mount Google Drive:

drive.mount('/content/drive')
Set up WebDriver and Chrome options:


chrome_options = webdriver.ChromeOptions()
chrome_options.add_argument('--headless')
chrome_options.add_argument('--no-sandbox')
chrome_options.add_argument('--disable-dev-shm-usage')
driver = webdriver.Chrome(options=chrome_options)
Navigate and login to the target website:

driver.get("https://www1.gsis.gr/gsisapps/psp/login/login.htm")
driver.find_element(By.NAME, "j_username").send_keys("your_username")
driver.find_element(By.NAME, "j_password").send_keys("your_password")
driver.find_element(By.CSS_SELECTOR, "input[type='submit']").click()
Scrape data and export to Excel:

The script will dynamically navigate through the website, click necessary buttons, and scrape data from the tables. The scraped data will be written to an Excel file located in your Google Drive.


# Locate elements and scrape data (example code block)
a_elements = driver.find_elements(By.XPATH, '//td/a')
workbook = xlsxwriter.Workbook('/content/drive/MyDrive/OLKES/files/rejections.xlsx')
worksheet = workbook.add_worksheet('rejections')
# Add your data scraping and writing logic here
workbook.close()
Quit the browser:

driver.quit()
Contributing
Contributions are welcome! Please fork the repository and use a feature branch. Pull requests are reviewed on a regular basis.

License
This project is licensed under the MIT License - see the LICENSE file for details.

Contact
If you have any questions or need further assistance, feel free to open an issue in the repository.

Replace "your_username" and "your_password" with actual login credentials. Adjust the URL and paths as necessary for your specific use case.
