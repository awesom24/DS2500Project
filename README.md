# Applying Wins Above Replacement (WAR) to the NBA
DS2500 Project - Vivek Divakarla, Daniel Draymore, Keshav Iyer, Jacob Norris, Jason Stitt

Northeastern University, Boston, MA, USA

Project originally done in 2021, updated in 2023 on the 2022-23 season data
### Introduction
In basketball, the goal of a team is to win games. As analytics have evolved, data scientists have started to heavily influence the sports world, with managers attempting to use data to improve teams. Wins Above Replacement (WAR) is a statistic that originates from baseball, with a goal to measure how much better a player is than an average replacement player would be. This metric aims to encompass all of the contributions a player has to a team, and thus is a very complex formula. The sabermetric community has spent years refining the formula for the baseball world. Our project was inspired by Keith Wollner's Value Over Replacement Player metric, referenced here https://en.wikipedia.org/wiki/Value_over_replacement_player
  However, the translation to the basketball world has not exactly happened. There are a few different WAR metrics, but they are very volume based, meaning the league’s stars who take a lot of shots per game will be at the top of the list, and their efficiency is not heavily factored. Tying back to the first paragraph, we wanted to create our own Wins Above Replacement metric incorporating efficiency, with the goal of trying to optimize a team’s assets/salary cap to create the best team they possibly can. After creating Efficiency WAR, we decided to model a Volume WAR that used popular NBA counting stats as opposed to efficiency. 

### Data Sources 
To start our project, we obtained our data from basketball reference [1], a website that tracks individual and team data in the NBA and has a wide variety of stats, both basic and advanced, to view. We then transferred the data we planned to use into .csv files and used these as the basis for our project. Using pandas in Python, we combined multiple csv files, with basic stats, advanced stats, and salary into one dataframe. Shown below is our dataframe, with key statistics for each player

![Screenshot 2023-11-21 at 3 48 52 PM](https://github.com/vivekdivakarla12/Applying-WAR-to-the-NBA/assets/11672096/97534ebc-b8f5-4bd2-bd77-6ddeee5baf37)

### Exploratory Data Analysis (EDA)
The first steps were to do exploratory data analysis on the dataset, and look for patterns between different variables. Shown below is a heatmap we used to analyze the relationship between stats. ![Screenshot 2023-11-21 at 4 07 17 PM](https://github.com/vivekdivakarla12/Applying-WAR-to-the-NBA/assets/11672096/ddab7ff2-adcb-4bfe-b2ee-f7f3073ac5c5)

### Creating the Metrics
After this, we had to decide which stats to use in our metric, and assign a weight for each one. For our first metric, we wanted to use percentages, and find a statistic of the players who are the most efficient. After making the calculations, we made it so the average player in the dataset had a 0.0 WAR, and plotted the distribution

<img width="593" alt="Screenshot 2023-11-22 at 11 05 15 AM" src="https://github.com/vivekdivakarla12/Applying-WAR-to-the-NBA/assets/11672096/56ed5e95-a991-479c-8f2b-d5882971aa56">

Compared to when the analysis was originally done on the 2021 season, there are not as many outliers, and the graph is more condensed. When we created the efficiency WAR metric, we then wanted to plot it compared to other variables to see the relationships. From this graph shown below, we can see that there is a bigger range of outcomes with the younger players, while the veterans are more consistent.

### Analysis
A second graph that we thought was important was plotting Efficiency WAR by team, and there were some interesting results. The NBA champion Nuggets were 2nd in WAR, and all of the top 6 teams made the playoffs. 3 of the 4 worst teams by record, the Hornets, Rockets, and Spurs, were in the bottom 4 in WAR as well. Our WAR metric possibly valued offense too much, as two teams with good offense but a bad defense and record (Pacers and Wizards) were top 10 in WAR. On the other end, two playoff teams that were great defensively, the Knicks and Heat, got bad ratings from our WAR metric. 

<img width="572" alt="Screenshot 2023-11-22 at 10 45 14 AM" src="https://github.com/vivekdivakarla12/Applying-WAR-to-the-NBA/assets/11672096/5ebdf067-3498-405e-96ad-1331e7241bb7">
<img width="965" alt="Screenshot 2023-11-22 at 11 10 55 AM" src="https://github.com/vivekdivakarla12/Applying-WAR-to-the-NBA/assets/11672096/5489a672-70d2-43ad-a713-e077c3880552">


The other metric we created to measure players is Volume WAR, which values totals and scoring. Some players were high on the efficiency WAR metrics but play less minutes and in garbage time so at times it does not accurately rate a player. As shown in the graph below, Volume WAR has a positive relationship with Field Goal Attempts, with some centers being outliers.

<img width="695" alt="Screenshot 2023-11-22 at 11 07 51 AM" src="https://github.com/vivekdivakarla12/Applying-WAR-to-the-NBA/assets/11672096/a6ddb1f5-544b-4dab-836e-89c26058b990">

### Conclusion and Next Steps
Through creating new and improved WAR metrics and applying them to the sport of basketball, we think teams can significantly increase their odds of winning a championship by drawing insights from this project. Our Efficiency WAR calculates which players win the most games for their team based on their efficiency. Our Volume WAR filters out the pool of players who only have efficient statistics because of the role they play on their team and upgrades those who put up high numbers, regardless of efficiency. NBA teams can use our algorithms to address their needs, by identifying  and acquiring players whose contracts fit their budgets and who will help them secure more wins. Teams should also give their current players with higher efficiency WAR’s more playing time. Taking these actions has the potential to vault a team up the standings and make them a legitimate annual contender to win the NBA Championship.

The next steps for this project would be to look at more seasons of data and readjust our weights based on those statistics. Our metric would become more consistent and useful if we incorporated more seasons. Another step we can take is to use our metric to try to predict what will happen in future seasons. 

