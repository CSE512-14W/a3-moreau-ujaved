a3-moreau-ujaved
===============

## Team Members

1. Thierry Moreau moreau@uw.edu
2. Umar Javed ujaved@uw.edu

## Overview

This stacked area visualization is constructed from the movie data set from assignment 2 (A2) available at the following location: http://courses.cs.washington.edu/courses/cse512/data/a2/movies.csv 

This data set combines varied statistics from different sources (IMDB, Rotten Tomatoes, The Numbers). It provides information on movies released from 1929 to 2011, including quantitative data on production budget, user ratings, gross, dvd sales but also nominal data such as genre. 

## Goal

The goal of our visualization tool is to provide viewers a timeline of aggregate statistics from the movie data set organized by genre. Users are given the choice to explore the movie release count, US gross, worldwide gross, production budget, IMDB ratings and Rotten Tomatoes ratings, grouped by movie genre and by release year. The user also can pick the aggregate function (sum, mean, median) applied to the specific statistic they wish to analyze. 

## Description

Our visualization tool provides the user with the following interactions:

1. Normalized and absolute stacked area views of aggregate statistics with multi-view mouse-over selection and labelling.  Normalizing the aggregate statistics helps preserve details for older movies statistics for which data is sparse. The sparsity on old movie information causes small variations to produce huge swings in the normalized view. Thus, we provide a second timeline displaying absolute (thus non-normalized) measures of the statistic they decide to explore. Providing multi-view mouse-over selection helps the user connect the normalized values with the absolute values.
2. The option to pick the statistic of interest (e.g. Production Budget, IMDB rating etc.). Transitions from one statistic to another allows the user to explore the data and compare and contrast various attributes. For instance the user can use the visualization tool to determine which genre is more popular under IMDB ratings vs. Rotten Tomatoes ratings, or which genre generates the most gross worldwide vs. in the U.S.
3. The option to pick the aggregate function of interest (sum, median and median). Providing mean and median aggregates on the statistics of interest allows the user to explore the movie data in more depth. For instance, despite the much lower number of releases, do documentaries on average get better ratings than comedies?
4. Brushing to select a period of interest. We provide a Context+Focus zooming where the absolute statistics window is used as a context window and the normalized statistics is used as the focus window. This interaction allows the users to focus the normalized stacked area plot on their decades of interest.


## Story Board

Our original source of inspiration is Google's Play Music Timeline: http://research.google.com/bigpicture/music/#

![googleTimeline](https://raw.github.com/CSE512-14W/a3-moreau-ujaved/master/figs/google_play_timeline.png)

This visualization, which is the result of a collaboration between two research groups at Google (Big Picture and Music Intelligence) "shows genres of music waxing and waning, based on how many Google Play Music users have an artist or album in their music library, and other data (such as album release dates). Each stripe on the graph represents a genre; the thickness of the stripe tells you roughly the popularity of music released in a given year in that genre."

This timeline was Thierry's source of inspiration for A2. He produced static renderings of the popularity of movie genres from 1960 to 2010. He explored two ways to define popularity. One would be based on ratings, and the other would be based on US gross. Although only one was submitted for A2, it was interesting to compare and contrast the two timelines. The static visualizations can be seen here: 

![grossing](https://raw.github.com/CSE512-14W/a3-moreau-ujaved/master/figs/A2-grossing.png) 
![ratings](https://raw.github.com/CSE512-14W/a3-moreau-ujaved/master/figs/A2-ratings.png)

We were motivated to deliver a visualization tool that would allow viewers to not only US gross or ratings, but all meaningful quantitative statistics extracted directly from CSV file grouped by year and genre. Smooth transitions between the views allow the user to perform qualitative comparisons between the statistics of interest. 

In A2, a lot of pre-processing was done in Tableau in order to export relevant data to a more flexible visualization tool. For this assignment, we wanted to process data directly from the raw csv file. There are two reasons for this: (1) the movie data set is small enough (~3200 lines) that it can quickly be processed in javascript, and (2) it would allow us to build a powerful data engine that would provide as much relevant information as possible to the user.

Because we chose to normalize the movie statistics, it was appropriate to add a second timeline describing absolute trends for direct comparison. 

* The user would be able to mouse-over the areas in the normalized timeline, and the matching area in the absolute timeline would be get highlighted
* The user would also be able to select an range of interest in the absolute timeline, which would cause the normalized timeline to focus onto the selected time-range.

Finally, to make it easy for the user to determine which area corresponds to what genre, we would provide a mouse-over tooltip displaying the specific genre of interest. This is particulary helpful for areas too small to contain a label.

The storyboard we formulated for this assignment can be viewed below:

![storyboard](https://raw.github.com/CSE512-14W/a3-moreau-ujaved/master/figs/storyboard.png) 

### Changes between Storyboard and the Final Implementation

The main feature that was dropped between the storyboard and the final implementation was the text labels on the area charts. We quickly realized it would be challenging to place text on areas in a way that labels would be unambiguous. We decided to go with a simple legend, which makes reading the chart unideal for the user since the user has to go back and forth between the chart and the legend to understand what each area corresponds to. Thankfully, the tool-tip provides quick labels to the user if she/he decides not to glance over the legend.

## Running Instructions

Our visualization is web based and can be accessed directly here: http://a3-moreau-ujaved.github.io/

To deploy the visualization, download the a3.html file along with the movies.csv data by running  `git clone https://github.com/CSE512-14W/a3-moreau-ujaved.git` and run `python -m SimpleHTTPServer 9000` and access this from http://localhost:9000/. You may have to rename a3.html to index.html.


## Development Process

We got to distribute the responsibilities quite evenly for the project. We found a good way to collaboratively work without spending too much time resolving conflicts. Thierry was in charge of the stacked area graph visualizations (static and transitions), the focus+context zooming/brushing. Umar was in charge of the data engine that extracts raw data from the csv dataset, the multi-view area selection and tooltip, and page presentation and layout.

Thierry's work breakdown (~20 hrs):

* Learning D3 (5hrs)
* Looking at examples and formulating objectives (1 hr with Umar)
* Basic stacked area (static + transitions) chart from example from a clean csv file (6hrs)
* Merging with Umar's data engine and fixing transitions (2 hrs)
* Context-focus view with brushing (6 hrs)

