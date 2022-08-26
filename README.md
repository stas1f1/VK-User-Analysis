# VK User Analysis

VK public pages have become quite a political battleground recently.
People will always engage in a heated discussion in the comments,
especially when their point of view is not shared by others. The 
question posed is - are they ***real*** people?
This project explores a possibility of bot account detection in 
those kinds of scenarios.

For this project, a [parsing script](https://github.com/stas1f1/VK-User-Analysis/blob/main/Parser_for_VK.ipynb)
based on VK Api and VKScript was created to collect posts data from 
a group of biggest and most active VK news (general and political) pages:

>1 канал, Лентач, РБК, Роскомсвобода, Дождь, Вести, Топор, Медуза, РенТВ, Плохие Новости, Life, РИА, Mash

Plus, we collected data about comments and respective user profiles (1,5M+ accounts total)
which accounted to 14+ GB of parquet data stored on cluster.

<p align="center">
  <img src="https://github.com/stas1f1/VK-User-Analysis/blob/main/acctypes.png" width="500" title="hover text">
</p>

Using Spark, we devised a series of criteria based on profile and 
activity data, and most intriguingly - comments sentiment analysis, 
performed with [Dostoevsky](https://github.com/bureaucratic-labs/dostoevsky) - a library for analysis of russian text (which I adore for its speed, accuracy and ease of use). With the gathered info we used a percentile score which gave us the final verdict.

Chosen groups come in varying degrees of negativity in audience

<p align="center">
  <img src="https://github.com/stas1f1/VK-User-Analysis/blob/main/pos_neg.png" width="500" title="hover text">
</p>

Below is the rating of groups based on spam comment ratio

<p align="center">
  <img src="https://github.com/stas1f1/VK-User-Analysis/blob/main/spamrates.png" width="500" title="hover text">
</p>

Want to take a deep dive into the pool of chaos? Here are the top-5 post that caused the most toxic, hateful and controversial discussions between people, trolls and bots:

**№1: "Плохие Новости", topic: Scandalous behavior in social media**

https://vk.com/public150709625?w=wall-150709625_8236914



**№2: "1 Канал", topic: Religious insults**

This post is somewhat of an outlier, as it dates back to 2012 and a bigger amount of accs are deleted

https://vk.com/public25380626?w=wall-25380626_79652



**№3: "РИА", topic: Event involving injury and reward of a police officer**

https://vk.com/public15755094?w=wall-15755094_33153186



**№4: "Плохие Новости", topic: Questional race-based statements**

https://vk.com/public150709625?w=wall-150709625_9340121



**№5: "Дождь\*", topic: Alexei Navalny's return to Russia**

*banned in Russia, only accessible with VPN

https://vk.com/public17568841?w=wall-17568841_6400781


---


Made with Python as a course project for 1st year of masters, FDT ITMO
