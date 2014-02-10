a3-moreau-ujaved
===============

## Team Members

1. Thierry Moreau moreau@uw.edu
2. Umar Javed ujaved@uw.edu

## Overview

This stacked area visualization is constructed from the movie data set from assignment 2 set at the following location: http://courses.cs.washington.edu/courses/cse512/data/a2/movies.csv This data set combines varied statistics from different sources (IMDB, Rotten Tomatoes, The Numbers). It includes information on movies released from 1929 to 2011, including production budget, user ratings, gross, dvd sales, and genre. 

The goal of our visualization tool is to provide viewers a timeline of aggregate statistics from the movie data set organized by genre. Users are given the choice to explore movie counts, US gross, worldwide gross, production budget, IMDB ratings and Rotten Tomatoes ratings, grouped by movie genre and by release year. The user also can pick the aggregate function (sum, mean, median) applied to the specific statistic they wish to explore. 

Our visualization tool provides the user with the following interactions:
1. Normalized and absolute stacked area views of aggregate statistics with multi-view mouse-over selection and labelling
    - Normalizing the aggregate statistics helps preserve details for older movies statistics for which data is sparse. Providing multi-view select helps the user connect the normalized values with the absolute values.
2. The option to pick the statistic of interest (e.g. Production Budget, IMDB rating etc.)
    - Transitions from one statistic to another allows the user to explore the data and compare and contrast various attributes (i.e. IMDB ratings vs. Rotten Tomatoes ratings, US gross vs. worldwide gross)
3. The option to pick the aggregate function of interest (sum, median and median)
    - Providing mean and median aggregates on the statistics of interest allows the user to explore the movie data in more depth
4. Brushing to select a time bound of interest 
    - This interaction allows the users to focus on their decades of interest.

## On the Visualization

Our original source of inspiration is Google's Play Music Timeline: http://research.google.com/bigpicture/music/#

![googleTimeline](https://raw.github.com/CSE512-14W/a3-moreau-ujaved/master/figs/google_play_timeline.png)

This visualization, which is the result of a collaboration between two research groups at Google (Big Picture and Music Intelligence) "shows genres of music waxing and waning, based on how many Google Play Music users have an artist or album in their music library, and other data (such as album release dates). Each stripe on the graph represents a genre; the thickness of the stripe tells you roughly the popularity of music released in a given year in that genre."

This timeline was Thierry's source of inspiration for A2. He produced static renderings of the popularity of movie genres from 1960 to 2010. He explored two ways to define popularity. One would be based on ratings, and the other would be based on US gross. Although only one was submitted for A2, it was interesting to compare and contrast the two timelines. The static visualizations can be seen here: 

![grossing](https://raw.github.com/CSE512-14W/a3-moreau-ujaved/master/figs/A2-grossing.png)
![ratings](https://raw.github.com/CSE512-14W/a3-moreau-ujaved/master/figs/A2-rating.png)

We were motivated to deliver a visualization tool that would allow viewers to not only US gross or ratings, but all meaningful quantitative statistics extracted directly from CSV file grouped by year and genre. In A2, a lot of pre-processing was done in Tableau in order to export relevant data to a more flexible visualization tool. For this assignment, we wanted to process data directly from the raw csv file. There are two reasons for this: (1) the movie data set is small enough (~3200 lines) that it can quickly be processed in javascript, and (2) it would allow us to build a powerful data engine that would provide as much relevant information as possible to the user.

As in Google's timeline, we decided to normalize our statistics because the information on older movies was quite sparse. The sparsity on old movie information causes small variations to produce huge swings in the normalized view. Thus, we provide a second timeline displaying absolute (thus non-normalized) measures of the statistic they decide to explore.

Conveniently, this second timeline is used as a context timeline for the user to select over their timeframe of interest they wish to focus on.


## Running Instructions

Put your running instructions here.  (Tell us how to open your visualization.) 

If your visualization is web-based,  it would be great if your submissions can be opened online. [Github Pages](http://pages.github.com/) is a good and easy way to put your visualization online so you can put your link here.  For example:

Access our visualization at http://cse512-14w.github.io/a3-jheer-kanitw/ or download this repository and run `python -m SimpleHTTPServer 9000` and access this from http://localhost:9000/.

(If you put your work online, please also write [one-line description and put a link to your final work](http://note.io/1n3u46s) so people can access it directly from CSE512-14W page.)

## Story Board

The original storyboard based itself a lot on the Google Play Music initial view timeline. Instead of only allowing the user to view one attribute (popularity), we decided to let the user chose as many attributes as we could process from the movie dataset csv file. 

Put either your storyboard content or a [link to your storyboard pdf file](storyboard.pdf?raw=true) here.   Just like A2, you can use any software to create a *reasonable* pdf storyboard.

### Changes between Storyboard and the Final Implementation

A paragraph explaining changes between the storyboard and the final implementation.

## Development Process

Include:
- Breakdown of how the work was split among the group members. 
- a commentary on the development process, including answers to the following questions: 
  - Roughly how much time did you spend developing your application?
  - What aspects took the most time?
