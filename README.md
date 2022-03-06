# MacBook-Data-Flipkart
## Procedure: 
```
•	Import selenium, Beautiful soup and Pandas packages using import
•	Now, automate a blank browser using browser = webdriver.Edge()
•	Initiate the required URL that we need to scrape using browser.get(“Laptops Online - Budget Laptops at Best Prices in India at Flipkart.com'’)
•	Get the html code of the page using soup = BeautifulSoup(browser.page_source, 'html.parser')
•	Go to the required webpage  right click and select inspect and hover the mouse and select the required data to scrape to locate the division and class for that particular data.
•	Now, lets scrape the product name and iterate for all using: [i.text.strip() for i in soup.select('div._4rR01T')]
•	Scrape and iterate the price using: [int(i.text.strip().replace('₹','').replace(',','')) for i in soup.select('div._30jeq3._1_WHN1')]
•	Follow the same procedure for Total ratings, Total reviews and Rating out of 5
•	The specs of the products are under UL (unordered list) and LI (list) tags.
•	So, first we need to go LI via UL using soup.select('ul._1xgFaf')[0]. find_all('li')[0].text.strip()
•	Define a function to combine all the scrapped data and store it in a dataframe using pd.DataFrame
•	Now, lastly import the dataframe to a csv file using .to_csv(‘file name’)
```
## Challenges Faced:
```
	In order to convert the price into integer we need to remove Rupee symbol and comma. So I used replace() function in order to get rid of both.
	Total_Ratings and Total_reviews are both in same div and same class. So, in order to get them I used split() and indexing to get them.
	It was difficult to iterate ul and li using list comprehension. So, I used to for loop and appended the data to the list comprehension in order to get the specs as it is.
	We can also use (ul.class)[0].text.strip() to get the specs, but It won’t be scraped as a list format.
```
