# README.md

## Summary

This visualization details the findings associated with the baseball.csv dataset by exploring the
different physical factors in the dataset and how they contribute to a player's number of career
homeruns and batting average (two metrics of batter performance). This dataset contains the 
fields "name","handedness","height","weight","avg", and "HR". These correspond to the player name, which hand 
they bat with, their height, weight, batting average, and number of homerruns respectively. 
An additional column ID was also added to provide a key for the unique rows in the file. 
The analysis follows an author-driven approach as it goes through each slide, followed by a 
user-driven slide selection approach at the end for the user to explore the dataset for 
themselves.

## Design

### Initial Revision
This visualization was designed to be viewed similarly to a slide deck. It begins with a title 
slide, followed by a slide that explains the dataset and which physical characteristics of the 
dataset were looked at. This is done purely through text. It then moves onto a slide that 
visualizes the distributions of both number of homeruns and batting average by player in 
the dataset. This is done to show the user what the average numbers look like, as well as what 
uncharacteristically good or bad values might look like. Afterwards, each of "height","weight",
and "handedness" are compared against the batting average and number of homeruns so that the
user can visualize how these physical characteristiscs map against player performance. 
Following this is a slide that describes the author's findings, along with buttons for the
user to explore any other part of the visualiazation.

All visualizations were designed as scatter plots with average lines to demonstrate a central 
measure of tendency for the distributions. For plots demonstrating a comparison of only 
two variables, black dots were chosen to provide a clear, unambiguous view of the distribution. 
An opacity value of 0.6 was used so that the density of the distribution could be easily determined 
by the viewer. For plots describing more than two variables, colours were assigned to the points 
to differentiate along with a legend to provide clarification of the colour assignments. Navigation
between slides was done using an individual button so that the user has no choice but to follow 
onto the next slide of the visualization. The button also gives the user as much time as they 
would like to view the slide, without making the user feel as though they are given too much 
or too little time as a timed slide might.

This visualization was designed using dimple.js to perform the plotting, and d3.js to perform 
the average lines, slide flow, and animations. The Jquery library was also used to perform 
some DOM manipulation (adding 'onclick' events). The rest of the visualization was designed 
in javascript. Timing for animations was done using d3's transition and delay functions.

The original iteration is saved as index_1.html.

### Revision Following Feedback 1

The primary points to address here were that the data points could be done using pictoral 
representations such as baseballs and players, and that the loading times between slides were long.

I decided not to change the visualizations to be pictoral since this would be very difficult 
to perform and would make it very difficult to convey the intended findings. In my opinion,
pictoral plots would appear too busy to convey any useful information about the distributions
or players.

In order to reduce load times, I decided to draw all data at once at the beginning, rather 
than on-demand as it was being done before. Doing so significantly reduced the loadtimes of the
analysis.

The revisions from this feedback were incorporated into index_2.html.

### Revision Following Feedback 2

The main points to address from this feedback were in regards to long load times,
inconsistencies in the loading of average lines, headers, etc., and visual
issues with the leading lines forming from .dimple-bubble classes.

As this feedback was given at the same time as for Feedback 1, the load times
are already corrected and so require no further revision.

The transitions to display headings and average lines were done intentionally
to draw the user's attention. However, based on this feedback, it seems
as though the transitions confuse the information that the user is 
intended to draw from the slides. I decided to remove these transitions from the
slides. The result of which can also be seen in index_2.html.

### Revision Following Feedback 3

The main points given in this feedback were to use an alternative to svg draw,
to include scroll indications for the stacked plots, to separate slides into
separate html pages, and to change the navigation on the last slide into
a navbar that is persistent throughout the slides.

An alternative to svg draw was not chosen since the purpose of this assignment
was to use d3.js and / or dimple.js, both of which use svg to draw the
visualizations.

Scroll indications were not implemented since responsive svg
was already incorporated so that plots would fit the height of the window
automatically. Though it does not adapt automatically if the user resizes their
window mid-session, I did not believe that this was necessary since the user
would likely be viewing it all at once.

Slides were not separated into separate html pages since I did not believe that
there was sufficient complexity or uniqueness to the slides to warrant the
added complications of linking multiple html pages.

The suggestion of switching the navigation buttons on the final slide into
a navbar that is persistent throughout the application was adopted. As well, though
it was not mentioned originally, I decided to implement a loading screen on the
main page so that the user would understand the long load times on the first
slide. These revisions can be found in index_3.html.

### Revision Following Feedback 4

As per the reviewer's feedback, formatting changes such as reduced opacity,
fixing cropped plot labels, and changing handedness labels from L,R,B
to Left, Right, and Both were made. Jitter was not added to the plots
since I could not determine a simple method to do so and I felt that
the necessity of jitter was less given the change that was made to
opacity.

Data with values of 0 for homeruns, avg, weight, or height were all removed
from the dataset since they represent either erroneous or missing data,
or players who did not actually play. Removing these values produces very
different relationships in the data, which are discussed in the conclusions slide.

The measure scales on the Homeruns vs. Batting average plot were changed
to be log scales as this reduces the plot density and displays the relationship
between the two series in a more logical manner. 

The reviewer suggested that a boxplot would be more effective at displaying the
relationship between performance and handedness. Taking this into consideration,
the plot on this slide was adapted into a boxplot using the d3plus library. It does
seem to convey the relationships in the data more effectively, provides
additional detail in regards to distribution statistics, and leads to
very different conclusions than those mentioned in the previous iteration
of the visualization. The conclusions slide was revised accordingly.

The reviewer also mentioned that the code should adhere to a style guide. The code
was made to more accurately reflect the recommended node.js style guide.

### Further revisions

At this time, index_4.html is the latest revision of this data visualization.

## Feedback

### Feedback 1
(From text message)
"So I looked at your website: the content is good, graphs were easy to understand. It 
could be more visually appealing (using baseballs and baseball players in the 
visualization). Also, it took a while to load from one page to the other."

### Feedback 2
(From Email)
"1. "Continue" slow from first page (not significant)
2. Question One:
a) when clicking on a player, the developing lines are slow in formation, also they do not
form in a linear progression. This appears only to occur in the top right quadrant marked 
by the average.
3. Question Two:
a) slow to load compared to question one. Similar issue regarding speed in the bottom right
quadrant this time. Appears to be because of the higher density of players in this quadrant.
4. Question Three:
a) very slow compared to last slide. Averages and continue button also populate following 
the chart. 
b) seems to be lag on all quadrants in comparison to the non-effected quadrants in question
one and two. 
4. Question Four:
a) same feedback as question three. Note that the lag for the lines following the selection
of a player only lag as the line extends to near the end of the graph.
5. Question Five:
a) Similar feedback to last slide.
6. Finding Page:
a) Nothing considerable--fluent. 

Overall, nothing too significant. The development of the lines for players selected should
be improved to make the website look more mature. Loading times, if improved, would make
the website much more fluent. Appearance is on point. Nothing else was spotted."

### Feedback 3
(From Email)
"On pages not using graphs (last page) use separate html page.
* Try using an alternative to svg draw - maybe static parts with a polite load could help.
* for pages that have multiple graphs, bring them side by side, it will help indicate that
you need to scroll to load. You can also indicate the need to scroll if you find it easier
to have them stack. 
* I would try making each graph into a separate html page - might help not having to clear
the script. also helps with debugging, you can localize problems with your timing between
graphs. 
* bring the blue menu from the last page into the header and keep it consistent between
the pages. good practice to have some sort of navigation so you don't trap people in a site. 

Looks great though dude!!"

### Feedback 4
Feedback 4 is included in the /feedback folder under the two files: 'udacity_review_06Jul2016.pdf' and 'udacity_code_review_06Jul2016.pdf'.
## Resources
http://stackoverflow.com/questions/29352970/dimple-js-add-vertical-line

This source was consulted to produce the average lines for the plot
