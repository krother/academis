
# Book Review: Python for Data Analysis

In the first half of 2015, I translated the book [Python for Data Analysis](http://shop.oreilly.com/product/0636920023784.do) by **Wes McKinney** to German together with **Christian Tismer**. A [book translation](http://www.oreilly.de/catalog/datenanalysemitpythonger/) is a great way to familarize with the content deeply. Here, I would like to share my insights.

## What is the book about?
Wes McKinney is the author of the [`pandas`](http://pandas.pydata.org/) Python library, and most of the book is about `pandas`. 

## Who is the book for?
If you are doing data analysis in Python, `pandas` will probably come your way at some moment. If you have a good command of basic Python and are looking to work with your data more efficiently, this book is for you. Everything shown is applicable to any field.

## What is pandas?
The `pandas` library gives you efficient table data structures in Python. At its core are the `Series` and `DataFrame` classes representing indexed columns and tables. From these you can quickly select, modify, aggregate and plot loads of data. If you are familiar with data frames in **R**, you got the idea.

`pandas` has been built on top of `numpy`, so most things are very fast. All `DataFrame` objects can be plotted easily. And the aggregation functions allow you to do even complicated things very quickly.

## What are the highlights in the book?

There are many highlights:

* Every chapter relies on one concrete data set, e.g. **Baby names from the last 130 years**, **Funds raised for presidential election campaigns**, **Incidents after the Haiti earthquake**. These are geeky data examples that make the book fun to read. I use some of these data sets in my courses regularly.
* I liked the introduction to the IPython shell a lot. You get introduced to a way of interactive coding that helps you to analyzing data more productively.
* There are dedicated chapters for advanced topics, such as working with **geospatial data** and **time series**.
* In the German translation, we made sure everything works **with Python3**.
* The code examples are available as [Jupyter notebooks](https://github.com/pydata/pydata-book).

## What are the caveats?

There are a few as well:

* `pandas` definitely has a steep learning curve. Writing a full book about it is more than justified. The library pushes the Python syntax to the limits, so that you can query your data concisely. This may feel a bit strange at first.
* For that reason, I wouldn't recommend the book to a novice programmer. There is a basic Python tutorial, but to code successfully with `pandas` you will need a bit of experience. I think having a background in any programming language is sufficient.
* Be prepared to **try the code examples right away**. The book has not been written to be digested on a beach. In my opinion, the book shines brightest when you dive into the data 
while reading and get your hands dirty.

## Conclusion

With **Python for Data Analysis**, Wes McKinney provides further support for his reputation as a data wizard who has a lot of tricks up his sleeves. Now You can learn quite a powerful bit of wizardry yourself.
