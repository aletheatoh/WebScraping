# FCC Archive Webscraping
Code to webscrape data from the Federal Communications Commission (FCC)'s Universal Licensing Archive System. 
## Built With
- Python 2.7
- Selenium 3.7.0
## Getting Started
### Preresquisites
- An IDE (Most Duke Students who have done CS101 and/or CS201 use Eclipse)
- Python 2.7 (Version used for CS101 @ Duke) 
- Selenium & Webdiver (i.e. Chrome, FireFox, Safari) extension
- xlrd (to read in data from excel spreadsheet database)
- xlwt (to generate excel spreadsheet output)
### Installing
- Python files
#### Important Note
This webscraper was built using Python 2.7, which does not easily read unicode strings. At present, this webscraper is not able to scrape data for 1510 companies whose names have non-ascii characters. It might be better to switch to Python 3 which has more unicode support. 

Reference: [Key differences between Python 2.7 and Python 3](https://www.digitalocean.com/community/tutorials/python-2-vs-python-3-practical-considerations-2)
## Running the Web Scraper
### Overview
#### Stating the file path
Basically, whenever you are opening a file, you need to reference the path of your directory. 
It is usually easiest if the file is in your current directory, as you simply have to state the file name, for example:
```
data = open_workbook('data.xlsx') 
```
If the file is located in another directory, you will need to state the file path, for example:
```
data = open_workbook('/Users/alethea/Documents/data.xlsx') 
```
However with chromedriver this is a little trickier. Chromedriver requires you to include the ChromeDriver location in your PATH environment variable:
```
chromedriver_path = '/Users/alethea/Documents/chromedriver'
driver = webdriver.Chrome(executable_path=chromedriver_path)
```
#### Code crashing?
Considering the fact that there are 4382 companies, you will mostly encounter TimeOutErrors. 
Fret not, the code has been designed such that in such an event, you can just run the code on companies you have not searched yet while retaining all previously scraped data. 
### What to amend in the code to work on your local environment
- WebScrapeMain.py
  - Line 149: amend ```chromedriver_path = '/Users/alethea/Documents/chromedriver'``` to state your ChromeDriver location
  - Line 152: amend ```data = open_workbook('data.xlsx')``` to state the file path of the excel workbook of licensees if it is not in your current directory
  - Lines 70 & 183: amend ```wb.save('/Users/alethea/Downloads/Spreadsheet_test.xls')``` to state which directory you want your data output to be located in. 
  - Line 153: **state the same file path in** ```visited_file = open_workbook('/Users/alethea/Documents/Spreadsheet_test.xls')``` **as the one stated in Lines 70 & 183**. This will make your life a lot easier in the event the code crashes.


- note that I'm using a mac

- handling timeouterrors
- installation guides
- fork github repo

- brief explanation of the different python files

There are 3 types of licenses. As they are each formatted differently, there are 3 separate python modules that contain a helper function to scrape each type of licence:
* call_sign.py - ```call_sign(driver, ws1, rowNum, colNum)``` 
* lease_id.py - ```lease_id(driver, ws1, rowNum, colNum)``` 
* tp_status.py - ```tp_status(driver, ws1, rowNum, colNum)``` 
