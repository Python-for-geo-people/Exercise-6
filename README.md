# Exercise 6: Analysing data using NumPy
This week we will continue working with real data files, but with NumPy instead of the basic Python tools.
We have two data files that we will load and analyse.
They should be somewhat familiar already.

## Sections
- [Problem 0: Creating a plotly account](#problem-0-creating-a-plotly-account)
- [Problem 1: NOAA climate data revisited](#problem-1-noaa-climate-data-revisited)
- [Problem 2: Volcanoes again? Dealing with tricky data files](#problem-2-volcanoes-again-dealing-with-tricky-data-files)
- [Optional tasks for advanced students](#optional-tasks-for-advanced-students)
- [Hints](#hints)
- [Your answers](#answers)

## Problem 0: Creating a plotly account
[plotly](https://plot.ly/) is a web-based platform for creating and sharing interactive graphs and presentations.
It also happens to have an easy-to-use function for exporting plots generated using the [Matplotlib plotting module](http://matplotlib.org/) (which we will see next week) to plotly.
We're going to experiment with using this, because we think interactive plotting on the web will become increasingly common in the future (plus it's cool!).
So, your first task in this week's exercise is to go to the plotly website and [create a free community account](https://plot.ly/accounts/login/?action=signup).
The instructions for doing so should be clear on the [plotly website](https://plot.ly/).

## Problem 1: NOAA climate data revisited
For this problem we are revisiting the data file used in Exercise 5.
As a reminder, you will be working with a climate data file from the [US National Oceanographic and Atmospheric Administration (NOAA) climate database](https://www.ncdc.noaa.gov/cdo-web/).
The data file [`816295.csv`](Data/816295.csv) comprises daily temperature measurements (in Fahrenheit) from several stations in the vicinity of the town of Ann Arbor, Michigan in the US from 1 January 1926 to 31 December 2015.

You job in this problem is to again calculate the mean annual winter and summer temperatures from 1926-2015.
*Again?!?*
Yes, but this time we're going to make a few changes to make better estimates.
Your script should:
1. Use the `np.loadtxt()` method to read in the [`816295.csv`](Data/816295.csv) data file ignoring the header.
2. Calculate the mean and standard deviation of the temperature values in the data file.
3. Remove any "bad" temperature values. Here, we will say that a "bad" temperature is any temperature high or lower than the mean plus or minus four times the standard deviation.
4. Sort the remaining data by the date.
5. Loop over all of the data by year and properly calculate the seasonal average temperatures.
In this case, the summer average temperature should include the months of June, July, and August.
The winter average temperature should include January, February, and December from the previous year.
Thus, you should only calculate seasonal averages for 1927 to 2015, since we have incomplete data for 1926 (no data for December 1925).
6. Use NumPy to write out the seasonal average data files for winter (`winter-avg-temps-numpy.csv`) and summer (`summer-avg-temps-numpy.csv`).
7. Save these files to your GitHub repository for this exercise.
Again, we will use these files next week when we explore plotting with Matplotlib.

## Problem 2: Volcanoes again? Dealing with tricky data files

## Optional tasks for advanced students

## Hints

# Answers
