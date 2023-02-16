# Exploratory analysis of the Polish parliament members and their Twitter data

### Project overview:
1. Scraping parliamentary data using Beautiful Soup
2. Crawling Twitter with Selenium and saving matching (verified) politician's Twitter handles
3. Using Twitter API to collect profile information and Tweets from politicans
4. Exploratory analysis of the data including age, education level, party affiliation, vote participation, number of Twitter followers etc.
5. Linear regression using OLS from statsmodels run to test for correlations
6. Wordcounts, cleaning, and stop-word removal run across the corpora of last 100 Tweets of each politician to find the most used phrases

<img width="900" alt="image" src="https://user-images.githubusercontent.com/32062967/219373731-1f8b2974-1244-4a4c-a1ce-f7a70beeae34.png">

## Project details

### Data 
he above dataframe consists of data collected on 1) governmental website of the parliament and 2) Twitter, via tweepy API.
Governmental website data includes politicians name, gender (binarised - calculated from the last letter of the name), party, role in their party, constituency, number of votes they got in last parliamentary election, previous terms as member of parliament, number of previous terms, date of birth, age, city of birth, education level, (binary) has_higher_education indicator, profession outside of government, number of parliamentary speeches, link to their speeches, percentage of parliamentary votes they took part in, link to their specific votes.
Twitter data includes, their nickname (handle), whether they are verified (that is everyone whose twitter account was found and saved), number of tweets, the last 100 tweets in one string, the most popular word in their tweets, number of instances of the most popular word, number of instances of the word ‘pis’ - the most popular word overall

### Data collection process
Governmental data was collected by first scraping a list of URLs to active members of parliament from https://www.sejm.gov.pl/Sejm9.nsf/poslowie.xsp?type=A with Beautiful Soup. Then, from each URL static information was scraped with Beautiful Soup and dynamic information (e.g. parliamentary speeches and votes) was collected with Selenium - automated browser clicked on elements to request information via ajax and then found appropriate data.

Twitter information was collected first by using Selenium to search for names of each person on Twitter in the “People” tab. Then, if the first result was a verified account, the user handle was saved to a dataframe. From there, tweepy was used to request the remaining data from Twitter API. All wordcount data was then based on the corpora of last 100 tweets of each user.

### Ethical considerations
I have no significant ethical concerns regarding this data and its collection process. To ensure this is the case, below I evaluate the process against 4 principles presented by Salganik (2017):
1. Respect for Persons - This research treats participants as autonomous and with respect. Gov- ernmental oﬀicials information is publicly available, similarly to Twitter users who accepted their terms and conditions and did not request to have their account made unavailable to API requests. Therefore this process does not extract any data that is not already public. 2. Beneficence - In the case of this exam, unless this project was pursued further, there are no direct benefits to the public or participants of this research. However, weighing this against the risks to anyone involved, this is not an ethical concern. 3. Justice - The distribution of benefits and burdens is not a significant concern. While I am the only real beneficiary in this case (unequal distribution), there is no bur- den or risk to the persons involved. 4. Respect for Law and Public Interest - This data collection process respects Twitter’s rules included in the robots.txt file. Furthermore, I believe it is in the public interest to understand how their elected parliament votes, who they are, and what do they say in the public space. This data collection process, therefore, respects the law and public interest.
