
# Coding Challenge: Lyrics Prediction

## Goal

In this challenge, you will build a simple predictor that can guess an artist from a pieces of lyrics. To do so, we need to write a program that collects lyrics from the web.

## Exercises

### Exercise 1

Go to the website [www.azlyrics.com](http://www.azlyrics.com/) and pick an artist.

### Exercise 2

Use the [requests](https://krother.gitbooks.io/python-3-module-examples/content/requests.html) module to download the page containing the list of songs for a given artist.

### Exercise 3

Have the program write the page to a file.

### Exercise 4

Use string functions to extract the hyperlinks. Find out which `href` fields link to individual songs and how to recognize them *unambiguously*.

### Exercise 5

Build a list of URLs for each song. Test one link manually.

### Exercise 6

Download the entire batch. Use the [time](https://krother.gitbooks.io/python-3-module-examples/content/time.html) module to wait 60 seconds after each download. **IF YOU OMIT THIS STEP THE SERVER WILL LOCK YOU OUT!**

### Exercise 7

Save all songs to separate HTML files.

### Exercise 8

Read all song files. Extract all lyrics as a list of strings.

### Exercise 9

Apply the recipe for a Bayesian classifier using the [Bag of Words recipe with scikit-learn](http://scikit-learn.org/stable/tutorial/text_analytics/working_with_text_data.html). Adjust the tutorial example to your own data.

### Improvements

### Exercise 1

Use [Regular Expressions](https://krother.gitbooks.io/python-3-module-examples/content/re.html) to extract the data.

### Exercise 2

Use [scrapy](https://scrapy.org/) to manage the download.

### Exercise 3

Remove non-meaningful characters from the text.

### Exercise 4

Try different model parameters.
