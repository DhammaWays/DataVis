## P6: Make Effective Data Visualization - Titanic Survivor Demographics Visualization
Lekhraj Sharma, July 2016, in fulfillment of [Udacity's Data Analyst Nanodegree](https://www.udacity.com/course/nd002)


### Summary

This survivor demographics visualization shows graphs for three categories of Titanic dataset. It shows survival information based on *sex*, *age group* and *cabin class (proxy for socio-economic status)*. It allows you to explore each of these categories interactively. You can also choose to see the survival information by either passenger count or percentage to find out which category survived better. **The main finding being conveyed in this visualization is that women, children and richer class survived better than others during titanic disaster**. *Which should not be too surprising!*

### Data

- [`titanic_train.csv`](https://raw.githubusercontent.com/DhammaWays/DataVis/master/project_P6/titanic_train.csv): Original downloaded training dataset from [kaggle](https://www.kaggle.com/c/titanic/data)

### Design

#### Exploratory Data Analysis

The training dataset downloaded from Kaggle was in good shape to start my exploration. I was already familiar with this dataset due to earlier courses. Used Microsoft Excel to quickly explore which categories of passengers survived better based on my earlier exposure to Titanic disaster story. While I did explore several variables of this data such as sex, age, Pclass, embarked, etc., I decided to focus on sex, age and Pclass (proxy to socio-economic status)  based on my intuition and earlier work with this dataset. Quick quantitative analysis seem to confirm my hypothesis that females, kids and rich folks survived better than others. I liked this finding as it is quite intuitive for others to grasp as well. Now my target was how to best visually represent this conclusion to others.

#### Data Visualization

##### Visual Encoding: Bar Chart Type
Next decision was on what kind of chart would convey clearly that women, children and richer class survived better than others. Since I wanted to highlight survived versus non-survived (died) for each of category, I wanted a representation that allowed viewer to make quick visual comparison call.  I settled on column stacked bar charts as they are good for showing a variable distribution broken down by another variable in single bar. Because bars have a great deal of visual weight and stand out so clearly as separate from one another, it is very easy to compare their lengths to determine the relative magnitudes of the values they encode. This easy visual comparison was crucial to convey my findings (e.g. women survived better than men).

##### Visual Encoding: Color
I choose variation of red and green to indicate those who did not survive versus those who did due to common semantic meaning of being dead and alive respectively. This way viewer does not have extra cognitive load of looking at legend to figure this out. Initially I chose color blind friendly variation of red (vermilion) and green (bluish green) but I changed them later on based on feedback to softer natural colors.

##### D3 or Dimple: Dimple
After trying out few initial visualization in **dimple.js**, I stuck to it as it kept meeting most of my needs as I progressed further. I did use **d3.js** later on for adding buttons to allow viewer to interactively explore the visualization.

##### New variables
Ended up creating a new variable called *AgeGroup* to classify passengers into **Adult** and **Children** to clearly show that **Children** survived better.

##### First Iteration
For initial iteration I just decide to show four charts side by side in a grid with each corresponding to overall survival rate and survival rate by sex, age group and passenger cabin class. I was *trying to establish that compared to overall casualty women, rich and children survived better*. I did have plan to make these graphs into an interactive graph in later iterations where a person can choose to drill down on gender, age group and passenger cabin class along with choice to see either actual count or % of survivors. I decided to go with these initial four graphs to see if my main message of women, children and richer class comes through in my choice of visual encoding.

This original iteration can be viewed at [`index_1.html`](http://htmlpreview.github.io/?https://github.com/DhammaWays/DataVis/blob/master/project_P6/index_1.html)

![First Iteration Image](https://raw.githubusercontent.com/DhammaWays/DataVis/master/project_P6/titanic_vis_1.png)

### Feedback

I posted my visualization for feedback in multiple places.

- [Udacity's Discussion Forum Thread 1](https://discussions.udacity.com/t/p6-request-for-feedback-titanic-survivor-demographics/174511)
- [Udacity's Discussion Forum Thread 2](https://discussions.udacity.com/t/request-for-feedback-p6-final-project-titanic-dataset-visualization/174883/5)
- [Udacity's Discussion Forum Thread 3](https://discussions.udacity.com/t/p6-final-project-titanic-dataset-visualization/176581)
- [Google+ community for Udacity's Data Analyst Nanodegree](https://plus.google.com/u/0/communities/116797052510270749486/stream/18cd20e1-64de-46d0-ad4e-6342f6abc284)


#### First Iteration Feedback

Overall five persons gave me some good feedback on my first iteration. Following is a summary of the feedback (actual feedback is available at above mentioned links).

##### Person #1 (JasonC)

> - I first notice that more women survived in raw number and percentage than men and opposite is true of 3rd class passengers. The bars are a good choice to show the difference between catagories. You may want to look into a grouped bar chart for an easier comparison of how many survived or didn't in each group.
> - I was able to draw conclusions from the data as displayed, though I do think that updating the tick labels and legend labels would help with quicker interpretation of the data.
> - Overall, it would seem that class above all else was the most likely determining factor with regard to a passenger's survival. It is difficult to tell with this version of the visualization, but it may become clear if you add percentages to each chart.
> - Overall, I like the direction of this! Adding the features you described in order to drive the story aspect of this will help in your final visualization.

##### Person #2 (Yanhua_Melody)

> - The stacked bar charts show clearly that the # of survivors in terms of gender, age and pclass.
> - It will be good if tooltips or the actual numbers were added to the graph to show the exact number for each stacked bar.
> - Using 0 and 1 to represent yes/no survived is a little confusing. I think it's better to just use "Yes" and "No" for the legend.
> - Color-wise I prefer not to use bright colors. In the link of the lecture there is an article named 'rules_for_using_color', highly recommend paper to read. Bright, dark colors are primarily useful for highlighting data in graphical displays, such as a particular set of bars, so I do suggest change the color of the bar charts to more natural ones.
> - Overall the charts are pretty informative and well-designed.

##### Person #3 (rkr1017_219823031791)

> - I think in general it conveys the trend of child, female and class higher rate of survival.
> - In your lower left plot it is not clear what age range is child and adult.
> - In my opinion it would be more informative to provide a rate of survival rather than absolute numbers, but I could be wrong.

##### Person #4 (leesh1215)

> - Like nobless oblige, Woman and child survive more than man and adult.
> - In the graph, about 50% children was dead in the sad disaster.
> - I want to know each Pclass child survive rate.
> - Graphs are easy to understanding. I want to know portion of the people in the graphs.

##### Person #5 (joseAR)

> - Overall looks good. The message that comes from the data is the survival outcome based on the different features of each passenger.
> - I would change the legends, where it shows Survived(1: Yes, 0:No), just put Survived, Not Survived in front of the colored rectangle and use that instead of having 0s and 1s.
> - On the axis labels, I would write "Age Group" and "Passenger Class". You have plenty of room in the visualization, there's no need to be shortening the labels.


#### Post First Iteration Feedback Design

I iterated further based on above feedback. Following are main changes:
- Combined different graphs into one graph with ability to *interactively* select between them via buttons on the side. Added main finding that "women, children and rich survived better" in sub-title of this new visualization.
- Allowed users to interactively show survival info across different categories (sex, age group, passenger cabin class).
- Allowed users to choose whether to show survival info as count or percentage for easy comparison across categories.
- Changed the legend, axis, hover tooltip labels to convey info better (e.g. Added age right next to Child to indicate what age group I was considering Child to be)
- Used more balanced natural colors.

The **second iteration** after above changes can be viewed at [`index_2.html`](http://htmlpreview.github.io/?https://github.com/DhammaWays/DataVis/blob/master/project_P6/index_2.html)

![Second Iteration Image](https://raw.githubusercontent.com/DhammaWays/DataVis/master/project_P6/titanic_vis_2.png)

#### Second Iteration Feedback

Overall three persons gave me some further feedback on my second iteration. Following is a summary of the feedback (actual feedback is available at forum  links).

##### Person #1 (andrey_2627821275964)

> - I do like your visualisation very much. It does demonstrate findings clearly.
> - There are several things which can be improved, as I take it you use pure D3: tooltips show "Survived: 0/1" - it may look better if it was something like "Survived: Y/N";
> - Also there is another piece of information "PassengerId: XYZ" in tooltips, I understand that it is passenger count and it would be clearer if it is called "Passenger count: XYZ".

##### Person #2 (adenguo)

> - Your visualization is good. I can read useful information from your visualization. I like the change between count and percentage.
> - The overall visualization is a little small. Most computer have a resolution above 1024*768. The svg element could be big as 1000*1000.
> - The legend text "Survived" is overlapped with the legend of died.
> - You could create some animation want the button is click. The effect of visualization will be more sound.

##### Person #3 (Ransford Hyman)

> - This is much more informative.   I was able to determine how you came to the conclusions of who were the most likely to survive.
> - One other suggestion I can make is that I believe that the count in each section is labeled "PassengerID"  I think that value should be renamed for clarity.
> - It might help to explain the Pclass variable as well.  Since I'm familiar with the dataset, I know that Pclass=1 is synonymous to First class, but someone new to it may not.
> - Looking good though!

#### Post Second Iteration Feedback Design

I iterated further based on above feedback from second iteration. Following are main changes:
- Updated hover tooltips to convey info better (e.g. Passenger Id to Passengers)
- Updated button and axis labels for *Pclass* to convey info better (e.g. Used First Class for 1, and so on)
- Increased the size of main chart and improved the spacing between different elements of the layout.
- Added animation for nicer transition between different graphs.

### Final Visualization

The **final visualization** after multiple iterations can be viewed at [`index.html`](http://htmlpreview.github.io/?https://github.com/DhammaWays/DataVis/blob/master/project_P6/index.html)


![Final Visualization Image](https://raw.githubusercontent.com/DhammaWays/DataVis/master/project_P6/titanic_vis.png)


### Resources

- [dimple.js](http://dimplejs.org/)
- [d3js](https://d3js.org/)
- [Udacity's Data Visualization and D3.js course](https://www.udacity.com/course/viewer#!/c-ud507-nd)
- [Choosing Colors](http://www.perceptualedge.com/articles/visual_business_intelligence/rules_for_using_color.pdf)
- [Colorblind Friendly Colors](http://jfly.iam.u-tokyo.ac.jp/color/#see)
- [Color Hex Values](http://www.colorhexa.com)
- [Choosing Chart Type](http://www.perceptualedge.com/articles/misc/Graph_Selection_Matrix.pdf)
- [Visual Encoding](http://www.perceptualedge.com/articles/b-eye/encoding_values_in_graph.pdf)
- [Top ten do's and don't for infographics](http://guides.library.duke.edu/datavis/topten)
- [Gestalt Principles](http://graphicdesign.spokanefalls.edu/tutorials/process/gestaltprinciples/gestaltprinc.htm)
