# ProjectDSCI100
dsci100 project
# Data Science Project: Planning Report  
UBC Minecraft Research Server  
Abhijeet Kaler 
DSCI 100
## 1. Data Description

For this project, I’m working with two datasets from a Minecraft research server run by a UBC Computer Science group. Basically, players volunteered to join this special server, their gameplay sessions were logged automatically, and they also filled out a short questionnaire about themselves. So the data mixes real behaviour with self-reported info, which is pretty cool and also something to keep in mind when thinking about data quality.

### players.csv  
This file has **196 players** and **7 variables**, with each row representing one unique player. The variables include:

- `experience` (factor): how experienced the player says they are at Minecraft (Beginner → Pro).  
- `subscribe` (logical): whether they opted into a game-related newsletter.  
- `hashedEmail` (ID): an random identifier used to link players to their sessions.  
- `played_hours` (numeric): total time the player spent on the research server.  
- `name` (character): first name only  
- `gender` (factor): reported gender.  
- `Age` (numeric): age in years.

### sessions.csv  
This second file contains **1535 rows** (one per session) and **5 variables**:

- `hashedEmail` (ID): connecting each session to a player.  
- `start_time`, `end_time` (character): timestamps for when the sessions began and ended.  
- `original_start_time`, `original_end_time` (numeric): timestamps in milliseconds since Unix epoch .

### Data issues I noticed
While exploring everything, a few problems popped up:

- Missing values: Some players didn’t report their age, and quite a few sessions are missing their end times—which means we have incomplete session durations.  
- Skewed distributions: `played_hours` is extremely skewed. Most players barely played, and a tiny handful played more, which is going to matter later for modelling.  
- Self-report bias: Experience level and gender rely on honesty. People might understate or overstate their skill, and that’s something we can’t directly check.  
- Selection bias: Since players had to voluntarily join this research server, they’re probably not representative of typical Minecraft players.  
- Name column is useless: It won’t help for any analysis and can introduce bias, so I won’t use it.

For the planning stage, I’m focusing on the player-level dataset (`players.csv`) because it contains the outcome I’m interested in however later, I’ll come back to `sessions.csv` to compute behavioural features by grouping sessions by `hashedEmail`.

Overall, the data is pretty clean, but these elements and biases are important to keep in mind before choosing a modelling approach.
