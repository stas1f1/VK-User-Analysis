# VK User Analysis

VK public pages have become quite a political battleground recently.
People will always engage in a heated discussion in the comments,
especially when their point of view is not shared by others. The 
question posed is - are they ***real*** people?
This project explores a possibility of bot account detection in 
those kinds of scenarios.

For this project, a [parsing script](https://github.com/stas1f1/VK-User-Analysis/blob/main/Parser_for_VK.ipynb)
based on VK Api and VKScript was created to collect posts data from 
a group of biggest and most active VK news and political pages:

>1 канал, Лентач, РБК, Роскомсвобода, Дождь, Вести, Топор, Медуза, РенТВ, Плохие Новости, Life, РИА, Mash

Plus, we collected data about comments and respective user profiles (3M+ active accounts total)
which accounted to 14+ GB of parquet data stored on cluster.

For each person, we defined a series of criteria based on profile and 
activity data, and most interestingly - comments sentiment analysis, 
performed with [Dostoevsky](https://github.com/bureaucratic-labs/dostoevsky) - a library for analysis of russian text which I highly adore for its speed and ease of use.

With the gathered info we used a percentile score which gave us the final verdict.
