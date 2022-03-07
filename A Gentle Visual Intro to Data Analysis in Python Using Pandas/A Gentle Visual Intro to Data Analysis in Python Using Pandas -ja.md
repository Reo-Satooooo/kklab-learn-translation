Discussions: [Hacker News (195 points, 51 comments)](https://news.ycombinator.com/item?id=18351685), [Reddit r/Python (140 points, 18 comments)](https://www.reddit.com/r/Python/comments/9scznd/a_gentle_visual_intro_to_data_analysis_in_python/)

If you’re planning to learn data analysis, machine learning, or data science tools in python, you’re most likely going to be using the wonderful [pandas](https://pandas.pydata.org/) library. Pandas is an open source library for data manipulation and analysis in python.

## Loading Data

One of the easiest ways to think about that, is that you can load tables (and excel files) and then slice and dice them in multiple ways:

![](https://jalammar.github.io/images/pandas-intro/0%20excel-to-pandas.png)

Pandas allows us to load a spreadsheet and manipulate it programmatically in python. The central concept in pandas is the type of object called a _DataFrame_ – basically a table of values which has a label for each row and column. Let’s load this basic CSV file containing data from a music streaming service:

```
df = pandas.read_csv('music.csv')
```

Now the variable `df` is a pandas DataFrame:

![](https://jalammar.github.io/images/pandas-intro/1%20view_pandas_dataframe.png)

## Selection

We can select any column using its label:

![](https://jalammar.github.io/images/pandas-intro/2%20select-column.png)

We can select one or multiple rows using their numbers:

![](https://jalammar.github.io/images/pandas-intro/3%20select-rows.png)

We can select any slice of the table using a both column label and row numbers using `loc` (but here it would be inclusive of both bounding row numbers):

![](https://jalammar.github.io/images/pandas-intro/4%20select_column-and-rows.png)

## Filtering

Now it gets more interesting. We can easily filter rows using the values of a specific row. For example, here are our jazz musicians:

![](https://jalammar.github.io/images/pandas-intro/pandas-filter-1.png)

Here are the artists who have more than 1,800,000 listeners:

![](https://jalammar.github.io/images/pandas-intro/5%20filter.png)

## Dealing with Missing Values

Many datasets you’ll deal with in your data science journey will have missing values. Let’s say our data frame has a missing value:

![](https://jalammar.github.io/images/pandas-intro/6%20set%20missing%20value.png)

Pandas provides multiple ways to deal with this. The easiest is to just drop rows with missing values:

![](https://jalammar.github.io/images/pandas-intro/7%20filter%20missing%20values.png)

Another way would be to fill-in the missing value using [`fillna()`](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.fillna.html) (with 0, for example).

## Grouping

Things start to get really interesting when you start grouping rows with certain criteria and aggregating their data. For example, let’s group our dataset by genre and see how many listeners and plays each genre has:

![](https://jalammar.github.io/images/pandas-intro/8%20group-by.png)

Pandas grouped the the two “Jazz” rows into one, and since we used `sum()` for aggregation, it added together the listeners and plays for the two Jazz artists and shows the sums in the combined Jazz column.

This is not only nifty, but is an extremely powerful data analysis method. Now that you know `groupby()`, you wield immense power to fold datasets and uncover insights from them. Aggregation is the first [pillar of statistical wisdom](https://www.amazon.com/Seven-Pillars-Statistical-Wisdom/dp/0674088913), and so is one of the foundational tools of statistics.

In addition to `sum()`, pandas provides multiple aggregation functions including `mean()` to compute the average value, `min()`, `max()`, and multiple other functions. More on `groupyby()` in the [Group By User Guide](https://pandas.pydata.org/pandas-docs/stable/groupby.html).

If you use `groupby()` to its full potential, and use nothing else in pandas, then you’d be putting pandas to great use. But the library can still offer you much, much more.

## Creating New Columns from Existing Columns

Often in the data analysis process, we find ourselves needing to create new columns from existing ones. Pandas makes this a breeze.

![](https://jalammar.github.io/images/pandas-intro/9%20create-new-column.png)

By telling Pandas to divide a column by another column, it realizes that we want to do is divide the individual values respectively (i.e. each row’s “Plays” value by that row’s “Listeners” value).

## Get Hands On!

You can get started playing with Pandas in your browser right now through this basic [notebook hosted in Google Colab](https://colab.research.google.com/github/jalammar/pandas-intro/blob/master/Pandas_Intro.ipynb). The notebook is also [available on Github](https://github.com/jalammar/pandas-intro/blob/master/Pandas_Intro.ipynb) if you have your local environment set up.

## Learn More Pandas

Want to learn more? Be sure to check out the [10 Minutes to pandas](https://pandas.pydata.org/pandas-docs/stable/10min.html) tutorial in the official Pandas docs. Thanks to [Marc Garcia](https://twitter.com/datapythonista) for initiating the thoughts for these visualizations and continuing to improve the pandas documentation.

## Your feedback is appreciated!

Did you find this tutorial helpful? Any suggestions for improvement? Please let me know ([@JayAlammar](https://twitter.com/JayAlammar)) know on Twitter. Thanks!