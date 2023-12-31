# PlagiarismChecker-ExpressJS
#### Expressjs nodejs server with API endpoint to run google search function and scraping main&amp;article text from top 10 browsed pages.
<br>
This Repo project is trying to solve https://www.codementor.io/projects/web/plagiarism-checker-website-atx32nf0oa 
<br>
### Introduction.
<br>
You'll be building an automated solution that handles plagiarism detection.
<br><br>
This might be used for publishing companies to replace a manual process in which they search for phrases from submitted manuscripts on Google to find pre-existing work.
<br><br>
### Requirements.
<br>
Your task is to build a web application where a user can upload a file (e.g. an MS Word document or Google Doc file) and get matches for similar content around the Internet.
<br><br>
In the back-end, your program should read the content from the uploaded file, extract some random phrases of around 5-10 words each, and run a Google search on them.
<br><br>
The program should then load the pages for each of the top five Google search results for each phrase and compare the content in that page with the content of the submitted file.
<br><br>
The program should then return a percentage of how similar the content is and also list the similar phrases and original URLs.<br><br>

#### More specifically, the program should:<br>
<br>
Consist of a web page where the user can upload a document.<br>
Extract random phrases from the document.<br>
Run a Google search against the random phrases.<br>
Scrape the content from the top five Google search results for each phrase.<br>
Clean the scraped content: remove headers etc, and just keep the main text.<br>
Compare the content of the submitted file with each of the scraped results. You can use any text similarity metric, or make this customisable.<br>
Return a percentage of how similar the uploaded content is to the scraped content.<br>
Return the similar parts of the content with a link to the original scraped URL.<br>
For an extra challenge: You can add a PDF generation pipeline that allows the user to download the results in a PDF formatted report.
<br>
<br><br><br>
## My solution

<br><br>
passing the search words as a query for the RunGoogleSearch function at '/api/google-search'.
<br> Puppeteer is a product for browser automation. When installed, it downloads a version of Chrome, which it then drives using puppeteer-core. Being an end-user product, puppeteer automates several workflows using reasonable defaults that can be customized.
<br>


https://github.com/Ebrahim-Ramadan/PlagiarismChecker-ExpressJS/assets/65041082/b494ea56-6b7b-4d8a-8629-fbd04201da83


<br>
By puppeteer, it retrieves the top 10 websites' links as results in google search, then <br> executing a concurrent functionality to visit each URL concurrently to improve the performance and reduce the overall scraping time. Concurrency allows you to process multiple URLs simultaneously, making the most of available system resources and network connections.
<br>
And, scraping the main context using certain CSS selectors like 'main'|'article'|'p'|... those selectors used by modular websites rn <br>
then finally writing into txt file the whole resulted texts appended so it becomes easier to search to see how many -only if- the search query exists in that txt file or not to ouput with the final percentage of the plagiarism
<br> The next missing is to implement a higher order func to accept paragraphs, split it into individual sentences so that each phrase runs the defined flow functions in this current repo. <br> that's the logic uf you guys have something better of implementation just fork
<br><br>

 https://github.com/Ebrahim-Ramadan/PlagiarismChecker-ExpressJS/assets/65041082/4346f5fe-dc44-4fd7-a307-b4f0ed8d2d78 
 
<br>

![Screenshot 2023-07-25 004058](https://github.com/Ebrahim-Ramadan/PlagiarismChecker-ExpressJS/assets/65041082/693821e0-5c3c-475e-8520-56144882663f)
![Screenshot 2023-07-25 004114](https://github.com/Ebrahim-Ramadan/PlagiarismChecker-ExpressJS/assets/65041082/80b1487c-5476-4996-b9b2-fe41da41c3ca)


<br>
<br>
the whole process takes around 2851.7ms per URL visit
<br>
<br>
day2=> Added TfIdf and cosine similarity to calculate the text similarity between the quered phrase and the significant words of the scrapped data -- step one to finalize the plagiarism checking percentage big part lets celebrate

<br><br><br>
## steps to follow
### make a GET request in postman (or whatever you're testing your API with) to that endpoint
<br>
http://localhost:3000/search/:query
<br>
with replacing query witht the URLencoded search phrase, you will be tracking the step-by-step process in the server log + scrapped resutls + urls wil appear at a json response in postman, too
