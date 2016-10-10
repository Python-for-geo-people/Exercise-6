# Exercise 6: Analysing data using NumPy
This week we will continue working with real data files, but with NumPy instead of the basic Python tools.
We have two data files that we will load and analyse.
They should be somewhat familiar already.
Note that you are only required to complete Problem 1.
Problem 2 is optional.

## Sections
- [Problem 0: Creating a plotly account](#problem-0-creating-a-plotly-account)
- [Problem 1: NOAA climate data revisited](#problem-1-noaa-climate-data-revisited)
- [Optional tasks for advanced students](#optional-tasks-for-advanced-students)
  - [Optional tasks for Problem 1](#optional-tasks-for-problem-1)
  - [(*Optional*) Problem 2: Volcanoes again? Dealing with tricky data files](#optional-problem-2-volcanoes-again-dealing-with-tricky-data-files)
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
Note that we only want the data for the dates and temperatures, not the entire contents of the data file.
2. Calculate the mean and standard deviation of the temperature values in the data file.
3. Remove any "bad" temperature values. Here, we will say that a "bad" temperature is any temperature high or lower than the mean plus or minus four times the standard deviation (μ ± 4σ).
4. Sort the remaining data by the date.
5. Loop over all of the data by year and properly calculate the seasonal average temperatures.
In this case, the summer average temperature should include the months of June, July, and August.
The winter average temperature should include January, February, and December from the previous year.
Thus, you should only calculate seasonal averages for 1927 to 2015, since we have incomplete data for 1926 (no data for December 1925).
6. Use the NumPy method `np.savetxt()` to write out the seasonal average data files for winter (`winter-avg-temps-numpy.csv`) and summer (`summer-avg-temps-numpy.csv`).
You may want to refer to the [NumPy documentation on `np.savetxt()`](http://docs.scipy.org/doc/numpy/reference/generated/numpy.savetxt.html) to see how it works, or use the object inspector in **Spyder**.
7. Save these files to your GitHub repository for this exercise.
Again, we will use these files next week when we explore plotting with Matplotlib.

**Note**: We are not creating annual data files this time, but simply working with the one larger data file.
This will take a bit of thought in terms of how to refer to certain months and years in the file, particularly since the default in NumPy is to load data as numerical values, not character strings.
In other words, you may want to refer to the [hints](https://github.com/Python-for-geo-people/Lesson-6-Intro-to-NumPy/blob/master/Lesson/hints.md) :smile:.

## Optional tasks for advanced students
### Optional tasks for Problem 1

- Define data types when reading in the data file by using the `dtype` option in `np.loadtxt()`.
You might consider defining the dates as type `int` and the temperatures as type `float`.
- Rather than appending to a list of seasonal average temperatures, define two empty NumPy arrays of the correct dimensions up front and use index values to fill the arrays with the years and seasonal average temperatures.
- Use the `fmt` option when saving the seasonal average data files using `np.savetxt()`.
With `fmt` you should be able to have nice integer values for the years and decimal values rounded to 1-2 decimal places for the average temperatures.

### (*Optional*) Problem 2: Volcanoes again? Dealing with tricky data files
**This problem is optional, just to be perfectly clear**.

Here we face the reality of a data file that contains not only non-numerical values, but also special characters (e.g., ö or é).
For this problem, we will use the [Smithsonian Institution's](http://volcano.si.edu/) complete Holocene volcano [database file `GVP-Volcano-List.csv`](Data/GVP-Volcano-List.csv).
For most files, there is not a problem to load the data using `np.loadtxt()` even if there are a mix of numerical and non-numerical values in the files.
However, if you try to load the `GVP-Volcano-List.csv` data file, which has special characters in some of the geographical data you will have trouble, even if you try to only load the "columns" containing numerical data such as the volcano ID, latitude, or elevation.

In this problem, you need to use the `np.genfromtxt()` method to load the `GVP-Volcano-List.csv` file, and ultimately manipulate the loaded data to reproduce the values in the `GVP-Volcano-Lat-Lon-Elev.csv` file.
To do this you should:

1. Load the `GVP-Volcano-List.csv` data file using the `np.genfromtxt()` method, skipping the header.
If you like, you can load only the "columns" from the file that contain the volcano ID, latitude, longitude, or elevation.
**Note**: The options for `np.genfromtxt()` differ slightly from `np.loadtxt()`, so you will likely need to refer to the [online documentation for `np.genfromtxt()`](http://docs.scipy.org/doc/numpy/reference/generated/numpy.genfromtxt.html).
2. Write out your new data file as `GVP-Volcano-Lat-Lon-Elev-NumPy.csv` using the `fmt` options to reproduce the formatting of the `GVP-Volcano-Lat-Lon-Elev.csv` file as closely as possible.
3. Compare the two files.
You can do this visually in a text editor or use the `diff` command in a Terminal window.
You can use `diff` as shown below:

    ```bash
    $ diff <file1> <file2>
    ```
The results will be a list of the differences in the two files on a character-by-character basis.
Note that if your output format for step 2 is different than the `GVP-Volcano-Lat-Lon-Elev.csv` file, you will see differences on every line.

## Hints
You can find some [hints for completing this week's exercise](https://github.com/Python-for-geo-people/Lesson-6-Intro-to-NumPy/blob/master/Lesson/hints.md) in the materials for Lesson 6.

# Answers
