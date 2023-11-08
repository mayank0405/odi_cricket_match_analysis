# ODI Cricket Matches Analysis (1971-2023) 

## Context

This extensive dataset provides a rich repository of historical information on One Day International (ODI) cricket matches played since 1971.

ODI cricket is known for its thrilling encounters, and this dataset captures the details of these matches comprehensively.

It is a valuable resource for cricket enthusiasts, statisticians, and analysts interested in exploring and analysing ODI cricket data.

**Key Features:**

- **Match Details:** Comprehensive information about each ODI match, including match date, location, and format.

- **Teams and Players:** Details of the participating teams, including player names, roles, and batting/bowling statistics.

- **Match Outcomes:** Information on match results, including the winning team and margin of victory.

- **Player of the Match:** Recognition of the standout player in each match.

- **Umpires and Match Referees:** Details of the officials responsible for overseeing the match.

- **Toss Details:** Insights into the toss winner's choice, influencing the course of the game.

- **Venue Information:** Location details, including stadium name, city, and country.

**Potential Use Cases:**

-   **Historical Analysis:** Study and analyze trends and patterns in ODI cricket over the years.
-   **Performance Evaluation:** Assess the performance of players and teams based on batting, and bowling statistics.
-   **Match Strategy:** Understand the impact of toss decisions on match outcomes.
-   **Fantasy Cricket:** Ideal for fantasy cricket enthusiasts looking to build teams based on historical player data.
-   **Sports Journalism:** Source of valuable data for sports journalists and writers.

Whether you're a cricket fan looking to relive the moments of classic matches or an analyst seeking insights, this dataset is a treasure trove of ODI cricket history.

Explore the world of ODI cricket, unravel the statistics, and enjoy the excitement of cricket matches spanning over five decades!

## Content: 

The following are the tables present in the dataset:

-  odi_Fow_Card.csv

- odi_Batting_Card.csv

- odi_Bowling_Card.csv

- odi_Matches_Data.csv

- odi_Partnership_Card.csv

- players_info.csv

The dataset for the following project can be found [here](https://www.kaggle.com/datasets/bhuvaneshprasad/odi-matches-historical-data-since-1971/code).

**_Since the dataset is huge, the results are also very large so for convenience we choose to show only a limited number of records in our queries and results._**

We have only used SQL for this project and on **Google BigQuery** platform.

**Author**: Mayank Singh

**Email**: mayanksingholive@gmail.com

**LinkedIn**: https://www.linkedin.com/in/mayank-singh-a71110156/

### :pushpin: Exploratory Analysis- 

#### :pushpin: How many tables are present in the database? 
````sql
SELECT
	table_catalog,
	table_schema,
	table_name
FROM  `sql-projects-403804.sports.INFORMATION_SCHEMA.TABLES`;
````
**_Results_**
| table_catalog       | table_schema | table_name  |
|---------------------|--------------|-------------|
| sql-projects-403804 | sports       | partnership |
| sql-projects-403804 | sports       | batting     |
| sql-projects-403804 | sports       | bowling     |
| sql-projects-403804 | sports       | matches     |
| sql-projects-403804 | sports       | fowl        |
| sql-projects-403804 | sports       | players     |

❗ **Insight-** The query gives us the tables present in the sports dataset. We use **_INFORMATION_SCHEMA.TABLES_** to get it.

#### :pushpin: How many columns and their datatypes are present in the tables?
````sql
SELECT
	table_name,
	column_name,
	ordinal_position,
	data_type
FROM  `sql-projects-403804.sports.INFORMATION_SCHEMA.COLUMNS`
WHERE  table_name = 'partnership';
````
**_Results_**
| table_name  | column_name       | ordinal_position | data_type |
|-------------|-------------------|------------------|-----------|
| partnership | Match_ID          | 1                | INT64     |
| partnership | innings           | 2                | INT64     |
| partnership | for_wicket        | 3                | FLOAT64   |
| partnership | team              | 4                | STRING    |
| partnership | opposition        | 5                | STRING    |
| partnership | player1           | 6                | FLOAT64   |
| partnership | player2           | 7                | FLOAT64   |
| partnership | player1_runs      | 8                | FLOAT64   |
| partnership | player2_runs      | 9                | FLOAT64   |
| partnership | player1_balls     | 10               | FLOAT64   |
| partnership | player2_balls     | 11               | FLOAT64   |
| partnership | partnership_runs  | 12               | FLOAT64   |
| partnership | partnership_balls | 13               | FLOAT64   |

````sql
SELECT
	table_name,
	column_name,
	ordinal_position,
	data_type
FROM  `sql-projects-403804.sports.INFORMATION_SCHEMA.COLUMNS`
WHERE  table_name = 'players';
````
**_Results_**
| table_name | column_name      | ordinal_position | data_type |
|------------|------------------|------------------|-----------|
| players    | player_id        | 1                | INT64     |
| players    | player_object_id | 2                | INT64     |
| players    | player_name      | 3                | STRING    |
| players    | dob              | 4                | DATE      |
| players    | dod              | 5                | DATE      |
| players    | gender           | 6                | STRING    |
| players    | batting_style    | 7                | STRING    |
| players    | bowling_style    | 8                | STRING    |
| players    | country_id       | 9                | FLOAT64   |
| players    | image_url        | 10               | STRING    |
| players    | image_metadata   | 11               | STRING    |


````sql
SELECT
	table_name,
	column_name,
	ordinal_position,
	data_type
FROM  `sql-projects-403804.sports.INFORMATION_SCHEMA.COLUMNS`
WHERE  table_name = 'matches';
````

**_Results_**
| table_name | column_name           | ordinal_position | data_type |
|------------|-----------------------|------------------|-----------|
| matches    | ODI_Match_No          | 1                | INT64     |
| matches    | Match_ID              | 2                | INT64     |
| matches    | Match_Name            | 3                | STRING    |
| matches    | Series_ID             | 4                | FLOAT64   |
| matches    | Series_Name           | 5                | STRING    |
| matches    | Match_Date            | 6                | DATE      |
| matches    | Match_Format          | 7                | STRING    |
| matches    | Team1_ID              | 8                | FLOAT64   |
| matches    | Team1_Name            | 9                | STRING    |
| matches    | Team1_Captain         | 10               | FLOAT64   |
| matches    | Team1_Runs_Scored     | 11               | FLOAT64   |
| matches    | Team1_Wickets_Fell    | 12               | FLOAT64   |
| matches    | Team1_Extras_Rec      | 13               | FLOAT64   |
| matches    | Team2_ID              | 14               | FLOAT64   |
| matches    | Team2_Name            | 15               | STRING    |
| matches    | Team2_Captain         | 16               | FLOAT64   |
| matches    | Team2_Runs_Scored     | 17               | FLOAT64   |
| matches    | Team2_Wickets_Fell    | 18               | FLOAT64   |
| matches    | Team2_Extras_Rec      | 19               | FLOAT64   |
| matches    | Match_Venue__Stadium_ | 20               | STRING    |
| matches    | Match_Venue__City_    | 21               | STRING    |
| matches    | Match_Venue__Country_ | 22               | STRING    |
| matches    | Umpire_1              | 23               | STRING    |
| matches    | Umpire_2              | 24               | STRING    |
| matches    | Match_Referee         | 25               | STRING    |
| matches    | Toss_Winner           | 26               | STRING    |
| matches    | Toss_Winner_Choice    | 27               | STRING    |
| matches    | Match_Winner          | 28               | STRING    |
| matches    | Match_Result_Text     | 29               | STRING    |
| matches    | MOM_Player            | 30               | FLOAT64   |
| matches    | Team1_Playing_11      | 31               | STRING    |
| matches    | Team2_Playing_11      | 32               | STRING    |
| matches    | Debut_Players         | 33               | STRING    |

````sql
SELECT
	table_name,
	column_name,
	ordinal_position,
	data_type
FROM  `sql-projects-403804.sports.INFORMATION_SCHEMA.COLUMNS`
WHERE  table_name = 'fowl';
````

**_Results_**

| table_name | column_name | ordinal_position | data_type |
|------------|-------------|------------------|-----------|
| fowl       | Match_ID    | 1                | INT64     |
| fowl       | innings     | 2                | INT64     |
| fowl       | team        | 3                | STRING    |
| fowl       | player      | 4                | FLOAT64   |
| fowl       | wicket      | 5                | FLOAT64   |
| fowl       | over        | 6                | FLOAT64   |
| fowl       | runs        | 7                | FLOAT64   |

````sql
SELECT
	table_name,
	column_name,
	ordinal_position,
	data_type
FROM  `sql-projects-403804.sports.INFORMATION_SCHEMA.COLUMNS`
WHERE  table_name = 'bowling';
````

**_Results_**

| table_name | column_name | ordinal_position | data_type |
|------------|-------------|------------------|-----------|
| bowling    | Match_ID    | 1                | INT64     |
| bowling    | innings     | 2                | INT64     |
| bowling    | team        | 3                | STRING    |
| bowling    | opposition  | 4                | STRING    |
| bowling    | name        | 5                | FLOAT64   |
| bowling    | overs       | 6                | FLOAT64   |
| bowling    | balls       | 7                | FLOAT64   |
| bowling    | maidens     | 8                | FLOAT64   |
| bowling    | conceded    | 9                | FLOAT64   |
| bowling    | wickets     | 10               | FLOAT64   |
| bowling    | economy     | 11               | FLOAT64   |
| bowling    | dots        | 12               | FLOAT64   |
| bowling    | fours       | 13               | FLOAT64   |
| bowling    | sixes       | 14               | FLOAT64   |
| bowling    | wides       | 15               | FLOAT64   |
| bowling    | noballs     | 16               | FLOAT64   |

````sql
SELECT
	table_name,
	column_name,
	ordinal_position,
	data_type
FROM  `sql-projects-403804.sports.INFORMATION_SCHEMA.COLUMNS`
WHERE  table_name = 'batting';
````

**_Results_**

| table_name | column_name | ordinal_position | data_type |
|------------|-------------|------------------|-----------|
| batting    | Match_ID    | 1                | INT64     |
| batting    | innings     | 2                | INT64     |
| batting    | team        | 3                | STRING    |
| batting    | batsman     | 4                | FLOAT64   |
| batting    | runs        | 5                | FLOAT64   |
| batting    | balls       | 6                | FLOAT64   |
| batting    | fours       | 7                | FLOAT64   |
| batting    | sixes       | 8                | FLOAT64   |
| batting    | strikeRate  | 9                | FLOAT64   |
| batting    | isOut       | 10               | BOOL      |
| batting    | wicketType  | 11               | STRING    |
| batting    | fielders    | 12               | STRING    |
| batting    | bowler      | 13               | FLOAT64   |


❗ **Insight-** In the above 6 queries, we have extracted the column name, ordinal position and data type of the columns of each table. We do it using **_INFORMATION_SCHEMA.COLUMNS_**.

### :pushpin: Total number of matches played:
````sql
SELECT  COUNT(*)  AS  number_of_matches
FROM  `sports.matches`;
````

**_Results_**
| number_of_matches |
|-------------------|
| 4686              |


❗ **Insight-** This query counts the number of matches played. This is done using the **_count_** function. Since all matches as unique and every record is a record of one match so, we use **_count(*)_**.

### :pushpin: Time Range: 
````sql
SELECT
	MIN(EXTRACT(YEAR  FROM  Match_Date))  AS  First_Year,
	MAX(EXTRACT(YEAR  FROM  Match_Date))  AS  Last_Year
FROM  `sports.matches`
WHERE  EXTRACT(YEAR  FROM  Match_Date)  IS  NOT  NULL;
````

**_Results_**
| First_Year | Last_Year |
|------------|-----------|
| 1971       | 2023      |

❗ **Insight-**  Given the huge period of time in the dataset we should know the first year when ODI matches started and the latest year ODI match happened.

### :pushpin: Number of matches played each year:
````sql
SELECT
	EXTRACT(YEAR  FROM  Match_Date)  AS  Year,
	COUNT(Match_ID)  AS  number_of_matches
FROM  `sports.matches`
GROUP  BY  1
ORDER  BY  1
LIMIT  5;
````

**_Results_**

| Year | number_of_matches |
|------|-------------------|
| 1    |                   |
| 1971 | 1                 |
| 1972 | 3                 |
| 1973 | 5                 |
| 1974 | 6                 |


❗ **Insight-** Here we try to find out the number of matches played every year from 1971. Since there are many records so we use **_limit 5_** to show only first 5 records. Also there is on _NULL_ value, this means that we don’t have data for that record.

### :pushpin: Find the number of matches played in each country:
````sql
SELECT
	Match_Venue__Country_,
	COUNT(Match_ID)  AS  number_of_matches_played
FROM  `sports.matches`
GROUP  BY  1
ORDER  BY  2  DESC
LIMIT  5;
````

**_Results_**

| Match_Venue__Country_ | number_of_matches_played |
|-----------------------|--------------------------|
| Australia             | 635                      |
| India                 | 507                      |
| England               | 500                      |
| United Arab Emirates  | 380                      |
| South Africa          | 378                      |

❗ **Insight-**  Next, we find out how many matches were held in each country since the inception of ODI Cricket. This gives us an understanding of how much ODI Cricket is popular in a given country. For this we use the  **_GROUP BY_**  function.

### :pushpin: Which venue hosted the maximum number of matches in the year 2016:
````sql
SELECT
	Match_Venue__City_,
	COUNT(Match_ID)  AS  number_of_matches
FROM  `sports.matches`
WHERE  EXTRACT(YEAR  FROM  Match_Date) = 2016
GROUP  BY  1
ORDER  BY  2  DESC
LIMIT  5;
````

**_Results_**

| Match_Venue__City_ | number_of_matches |
|--------------------|-------------------|
| Edinburgh          | 6                 |
| Dhaka              | 5                 |
| Harare             | 5                 |
| Sharjah            | 5                 |
| Bulawayo           | 5                 |

❗ **Insight-** In order to find out the number of matches held in each venue in the world we do the same process as done before but here we do it only for the year 2016. We put the condition in the where clause using **_extract_** function.

### :pushpin: Find the number of tied matches:
````sql
SELECT  COUNT(Match_ID)  AS  number_of_matches
FROM  `sports.matches`
WHERE  Match_Result_Text = 'Match tied';
````

**_Results_**
| number_of_matches |
|-------------------|
| 36                |

❗ **Insight-**  Here we try to find out the number of tied matches since the starting of ODI cricket. This is a very fascinating thing that in so many matches played since 1971 only 36 matches have been tied.

### :pushpin: What is the number of matches won and lost by teams who won the toss:
````sql
SELECT
	SUM(CASE  WHEN  Toss_Winner = Match_Winner  THEN  1  END)  AS  matches_won,
	SUM(CASE  WHEN  Toss_Winner <> Match_Winner  THEN  1  END)  AS  matches_lost
FROM  `sports.matches`
WHERE  Toss_Winner  IS  NOT  NULL  AND  Match_Winner  IS  NOT  NULL;
````

**_Results_**

| matches_won | matches_lost |
|-------------|--------------|
| 2251        | 2227         |

❗  **Insight-** Here we have to find how many matches were won and lost by the team that won coin toss. For that we use the **_CASE_** to do the condition checking and then use the **_SUM()_** function to find the total number of matches.

### :pushpin: Find the number of matches in which players made their debut:
````sql
SELECT  COUNT(LENGTH(Debut_Players))  AS  number_of_matches
FROM  `sports.matches`
WHERE  LENGTH(Debut_Players)  >  2;
````

**_Results_**

| number_of_matches |
|-------------------|
| 1575              |

❗ **Insight-** Here we use the **_count_** and **_length_** function to find out in how many ODI matches, players made their debut. We **_use length(Debut_Players) > 2_** because values stored in **_Debut_Players_** are string and if anyone has made debut, his id stored as string. So, if there are any values in debut_players, their length must be greater than 2 because if there is no one then the value is ‘[]’.

### :pushpin: During which innings maximum number of fowls happened:
````sql
SELECT
	innings,
	COUNT(Match_ID)  AS  number_of_fowls
FROM  `sports.fowl`
GROUP  BY  innings
ORDER  BY  2  DESC;
````

**_Results_**

| innings | number_of_fowls |
|---------|-----------------|
| 1       | 36366           |
| 2       | 30754           |

❗ **Insight-**  Here we find out the number of fowls happened in each innings of all the match and then order by number_of_fowls. This shows that most fowls happened during first innings.

### :pushpin: Find the details of the matches during which highest number of runs were scored by both the teams:
````sql
WITH  cte  AS  (
		SELECT  *
		FROM  `sports.batting`
		WHERE
			team  IS  NOT  NULL
			AND  batsman  IS  NOT  NULL
			AND  runs  IS  NOT  NULL
			AND  balls  IS  NOT  NULL
			AND  fours  IS  NOT  NULL
			AND  sixes  IS  NOT  NULL
			AND  strikeRate  IS  NOT  NULL
)

SELECT
	c.Match_ID,
	m.Match_Date,
	m.Series_Name,
	SUM(c.runs)  AS  runs
FROM  cte  c
INNER  JOIN  `sports.matches`  m  ON  c.Match_id = m.Match_ID
GROUP  BY  1, 2, 3
ORDER  BY  4  DESC
LIMIT  5;
````

**_Results_**

| Match_ID | Match_Date | Series_Name                                      | runs  |
|----------|------------|--------------------------------------------------|-------|
| 238200   | 2006-03-12 | Australia tour of South Africa  - 2006 (2005/06) | 833.0 |
| 1158069  | 2019-02-27 | England tour of WI  - 2019 (2018/19)             | 778.0 |
| 430886   | 2009-12-15 | Sri Lanka tour of India  - 2009 (2009/10)        | 777.0 |
| 743945   | 2015-06-12 | New Zealand tour of England  - 2015 (2015)       | 736.0 |
| 1384418  | 2023-10-28 | ICC Cricket World Cup in India - 2023 (2023/24)  | 736.0 |


 ❗ **Insight-** Here we have to find out the matches and the series in which highest number of runs were scored. For this we use **_windows function_** and **_INNER JOIN_** between matches table and **_cte_** on _Match_ID_. We then show the result in the descending order of runs accumulated.

### :pushpin: During which series the maximum number of ODI matches were played(give top 5):
````sql
WITH cte AS (
    SELECT *
    FROM `sports.batting`
    WHERE
        team IS NOT NULL
        AND batsman IS NOT NULL
        AND runs IS NOT NULL
        AND balls IS NOT NULL
        AND fours IS NOT NULL
        AND sixes IS NOT NULL
        AND strikeRate IS NOT NULL
)

SELECT
    m.Series_Name,
    COUNT(DISTINCT m.Match_ID) AS num_matches
FROM `sports.matches` m
INNER JOIN cte c ON m.Match_ID = c.Match_ID
GROUP BY 1
ORDER BY 2 DESC
LIMIT 5;
````

**_Results_**

| Series_Name                                                          | num_matches |
|----------------------------------------------------------------------|-------------|
| World Cup League 2  - 2019 (2019-2023)                               | 124         |
| ICC World Cup in Kenya/South Africa/Zimbabwe - 2003 (2002/03)        | 52          |
| ICC World Cup in West Indies - 2007 (2006/07)                        | 51          |
| ICC Cricket World Cup in Bangladesh/India/Sri Lanka - 2011 (2010/11) | 49          |
| ICC Cricket World Cup in Australia/New Zealand - 2015 (2014/15)      | 48          |

❗ **Insight-**  We have to find out which ODI Series is the most popular. This will help us in generating more income for the countries since it will tell us which kind of tournaments should we popularize more. As we did in the previous query, we use **_windows function_** and **_INNER JOIN_** on _Match_ID_. And then in the _SELECT_ clause we use **_COUNT()_** function. From this analysis we find out that World Cup Super League 2 is the most popular with 124 matches.

### :pushpin: Find out the details of the top 5 batsmen who scored highest runs in a series:
````sql
WITH cte AS (
    SELECT *
    FROM `sports.batting`
    WHERE
        team IS NOT NULL
        AND batsman IS NOT NULL
        AND runs IS NOT NULL
        AND balls IS NOT NULL
        AND fours IS NOT NULL
        AND sixes IS NOT NULL
        AND strikeRate IS NOT NULL
)

SELECT
    c.batsman,
    c.team,
    m.Series_Name,
    SUM(c.runs) AS runs
FROM `sports.matches` m
INNER JOIN cte c ON m.Match_ID = c.Match_ID
GROUP BY 1, 2, 3
ORDER BY 4 DESC
LIMIT 5;
````

**_Results_**

| batsman  | team    | Series_Name                            | runs   |
|----------|---------|----------------------------------------|--------|
| 65478.0  | Namibia | World Cup League 2  - 2019 (2019-2023) | 1298.0 |
| 47469.0  | P.N.G.  | World Cup League 2  - 2019 (2019-2023) | 1290.0 |
| 103569.0 | U.S.A.  | World Cup League 2  - 2019 (2019-2023) | 1219.0 |
| 88991.0  | U.S.A.  | World Cup League 2  - 2019 (2019-2023) | 1184.0 |
| 53016.0  | Oman    | World Cup League 2  - 2019 (2019-2023) | 1098.0 |

❗ **Insight-**  Here we have to find the batsman who scored the highest number of runs from each team in a given series. For this we use the same previous methods but use **_SUM_** function over runs.

### :pushpin: During which series the bowlers gave their best performance:
````sql
SELECT
    m.Series_Name,
    ROUND(AVG(s.economy), 2) AS average_economy
FROM `sports.bowling` s
INNER JOIN `sports.matches` m ON s.Match_ID = m.Match_ID
WHERE s.economy > 0
GROUP BY 1
ORDER BY 2
LIMIT 5;
````

**_Results_**

| Series_Name                                   | average_economy |
|-----------------------------------------------|-----------------|
| England tour of Ireland  - 2015 (2015)        | 2.85            |
| England tour of Australia  - 1978 (1978/79)   | 2.9             |
| England tour of West Indies  - 1981 (1980/81) | 3.04            |
| Pakistan tour of England  - 1978 (1978)       | 3.07            |
| India tour of Sri Lanka  - 2006 (2006)        | 3.1             |

❗ **Insight-**  In order to find that the bowlers gave their best performance, we have to look at the economy rate. Economy in cricket means average number of runs conceded by bowlers per over. If we find the average economy of bowlers for each series and then order by **average_economy** to get the lowest average. From this we find out that bowlers were most economical during England Tour of Ireland in 2015 with an exceptional economy of 2.85.

### :pushpin: Find the series in year 2023 where the total number of wickets taken is greater than 100:
````sql
SELECT
    m.Series_Name,
    SUM(b.wickets) AS wickets
FROM `sports.matches` m
INNER JOIN `sports.bowling` b ON m.Match_ID = b.Match_ID
WHERE EXTRACT(YEAR FROM m.Match_Date) = 2023
    AND m.Series_Name LIKE "%World Cup%"
GROUP BY 1
HAVING SUM(b.wickets) > 100
ORDER BY 2 ASC;
````

**_Results_**

| Series_Name                                                                                                                                                   | wickets |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------|---------|
| "ICC Cricket World Cup Qualifier Play-off Canada, Jersey, Namibia, Papua New Guinea, United Arab Emirates, United States of America in Namibia - 2023 (2023)" | 234.0   |
| World Cup League 2  - 2019 (2019-2023)                                                                                                                        | 301.0   |
| ICC Cricket World Cup in India - 2023 (2023/24)                                                                                                               | 431.0   |
| ICC Cricket World Cup Qualifier in Zimbabwe - 2023 (2023)                                                                                                     | 484.0   |

❗ **Insight-**  Here it was asked to find out the series where the total number of wickets taken are greater than 100. So, for that condition, we have used HAVING function to see whether the sum is greater than 100 or not.

### :pushpin: What is the trend in number of fowls happened in matches from 2010 to 2020:
````sql
WITH matches_per_year AS (
    SELECT
        EXTRACT(YEAR FROM Match_Date) AS year,
        COUNT(f.Match_ID) AS num_matches
    FROM `sports.matches` m
    INNER JOIN `sports.fowl` f ON m.Match_ID = f.Match_ID
    WHERE EXTRACT(YEAR FROM Match_Date) IS NOT NULL
        AND EXTRACT(YEAR FROM Match_Date) BETWEEN 2010 AND 2020
    GROUP BY 1
)

SELECT
    year,
    num_matches,
    ROW_NUMBER() OVER (ORDER BY num_matches) AS rank
FROM matches_per_year;
````

**_Results_**

| year | num_matches | rank |
|------|-------------|------|
| 2020 | 646         | 1    |
| 2012 | 1269        | 2    |
| 2016 | 1468        | 3    |
| 2014 | 1793        | 4    |
| 2017 | 1807        | 5    |
| 2018 | 1904        | 6    |
| 2013 | 1941        | 7    |
| 2010 | 2091        | 8    |
| 2015 | 2098        | 9    |
| 2011 | 2135        | 10   |
| 2019 | 2136        | 11   |

❗ **Insight-**  We have to find out the trend in number of fowls over a given period of time. For that we use the **_row_number()_** function to see whether it gives us some ranking in the matches with most number of fowls. Unfortunately, even though we get a ranking on the basis of number of matches with fowls we still don’t see a trend or a pattern. It is very uneven so, we can’t say anything about the trend.

### :pushpin: Find the details of the batsmen who were the highest run scorers in a given series:
````sql
WITH cte AS (
    SELECT
        m.Series_Name,
        EXTRACT(YEAR FROM m.Match_Date) AS series_year,
        b.batsman,
        SUM(b.runs) AS runs
    FROM `sports.matches` m
    INNER JOIN `sports.batting` b ON m.Match_ID = b.Match_ID
    WHERE EXTRACT(YEAR FROM m.Match_Date) IS NOT NULL
    GROUP BY 1, 2, 3
),
cte2 AS (
    SELECT
        Series_name,
        series_year,
        batsman,
        runs
    FROM (
        SELECT
            Series_Name,
            series_year,
            batsman,
            runs,
            DENSE_RANK() OVER (PARTITION BY Series_Name, series_year ORDER BY runs DESC) AS rnk
        FROM cte
        ORDER BY 2
    ) t
    WHERE rnk = 1
)

SELECT
    c.Series_name,
    c.series_year,
    p.player_name,
    p.dob,
    p.gender,
    p.batting_style,
    p.bowling_style
FROM cte2 c
INNER JOIN `sports.players` p ON c.batsman = p.player_id
WHERE c.series_year BETWEEN 2007 AND 2009
ORDER BY 2
LIMIT 5;
````

**_Results_**

| Series_name                                                                          | series_year | player_name      | dob        | gender | batting_style  | bowling_style         |
|--------------------------------------------------------------------------------------|-------------|------------------|------------|--------|----------------|-----------------------|
| "Associates Tri-Series (in Kenya) Canada, Kenya, Scotland in Kenya - 2007 (2006/07)" | 2007        | Ravi Shah        | 1972-08-28 | M      | right-hand bat | right-arm medium-fast |
| Australia tour of India  - 2007 (2007/08)                                            | 2007        | Andrew Symonds   | 1975-06-09 | M      | right-hand bat | right-arm medium      |
| New Zealand tour of Australia  - 2007 (2007/08)                                      | 2007        | Ricky Ponting    | 1974-12-19 | M      | right-hand bat | right-arm medium      |
| Sri Lanka tour of New Zealand  - 2006 (2006/07)                                      | 2007        | Kumar Sangakkara | 1977-10-27 | M      | left-hand bat  | right-arm offbreak    |
| South Africa tour of Zimbabwe  - 2007 (2007)                                         | 2007        | Tatenda Taibu    | 1983-05-14 | M      | right-hand bat | right-arm medium      |


❗ **Insight-**  Here we find out the details of the batsman who scored most runs in a series. This will help the selectors in deciding which batsman to pick and which to drop on the basis of number of runs scored. For convenience we decide to show only 5 records.

### :pushpin: Find the details of the bowlers who were most economical during a given series:
````sql
WITH CTE AS (
    SELECT
        m.Series_Name,
        EXTRACT(YEAR FROM m.Match_Date) AS Series_year,
        o.name,
        ROUND(AVG(o.economy), 2) AS economy,
        SUM(o.wickets) AS wickets,
        RANK() OVER (PARTITION BY m.Series_Name, EXTRACT(YEAR FROM m.Match_Date) ORDER BY SUM(o.wickets) DESC, AVG(o.economy)) AS rnk
    FROM `sports.matches` m
    INNER JOIN `sports.bowling` o ON m.Match_ID = o.Match_ID
    WHERE EXTRACT(YEAR FROM m.Match_Date) IS NOT NULL
    GROUP BY 1, 2, 3, m.Match_Date
),
CTE2 AS (
    SELECT
        Series_Name,
        Series_year,
        name,
        economy,
        wickets
    FROM (
        SELECT
            Series_Name,
            Series_year,
            name,
            economy,
            wickets,
            rnk
        FROM CTE
        WHERE rnk = 1
    ) t
)
SELECT
    c.Series_Name,
    c.Series_year,
    p.player_name,
    c.economy,
    c.wickets,
    p.dob,
    p.gender,
    p.batting_style,
    p.bowling_style
FROM CTE2 c
INNER JOIN `sports.players` p ON c.name = p.player_id
ORDER BY c.Series_year
LIMIT 5;
````

**_Results_** 

| Series_Name                                                           | Series_year | player_name     | economy | wickets | dob        | gender | batting_style  | bowling_style          |
|-----------------------------------------------------------------------|-------------|-----------------|---------|---------|------------|--------|----------------|------------------------|
| England [Marylebone Cricket Club] tour of Australia  - 1970 (1970/71) | 1971        | Ashley Mallett  | 3.18    | 3.0     | 1945-07-13 | M      | right-hand bat | right-arm offbreak     |
| Australia tour of England and Scotland  - 1972 (1972)                 | 1972        | Geoff Arnold    | 2.45    | 4.0     | 1944-09-03 | M      | right-hand bat | right-arm fast-medium  |
| Pakistan tour of New Zealand  - 1973 (1972/73)                        | 1973        | Dayle Hadlee    | 3.18    | 4.0     | 1948-01-06 | M      | right-hand bat | right-arm medium-fast  |
| West Indies tour of England  - 1973 (1973)                            | 1973        | Derek Underwood | 2.72    | 3.0     | 1945-06-08 | M      | right-hand bat | slow left-arm orthodox |
| New Zealand tour of England  - 1973 (1973)                            | 1973        | John Snow       | 3.2     | 4.0     | 1941-10-13 | M      | right-hand bat | right-arm fast-medium  |

❗ **Insight-** Here we have to find out the bowlers who were economical during a given series. One thing to note here is that a batsman who are part time bowlers can also have very good statistics. So, we will also use number of wickets taken and economy rate to find out the players who are only bowlers. We order them by number of wickets in **_descending_** order and then economy in **_ascending_** to find out the bowler with best numbers in a given series. This helps us in finding which countries have the best bowlers.

### :pushpin: Find the details of the match that had the highest batting partnership in a series:
````sql
WITH partnership AS (
    SELECT
        Match_ID,
        innings,
        team,
        player1,
        player2,
        partnership_runs,
        partnership_balls
    FROM
        `sports.partnership`
),

ranking AS (
    SELECT
        Match_ID,
        Series_Name,
        team,
        player1,
        player2,
        partnership_runs,
        partnership_balls,
        ROW_NUMBER() OVER (PARTITION BY Match_ID, Series_Name, innings ORDER BY partnership_runs DESC) AS rnk
    FROM (
        SELECT
            m.Match_ID,
            m.Series_Name,
            p.team,
            p.innings,
            p.player1,
            p.player2,
            p.partnership_runs,
            p.partnership_balls
        FROM
            `sports.matches` m
        INNER JOIN partnership p ON m.Match_ID = p.Match_ID
        WHERE
            Series_Name <> '  -  ()'
    ) t
)

SELECT
    Match_ID,
    Series_Name,
    team,
    partnership_runs AS runs_scored,
    partnership_balls AS balls_faced
FROM
    ranking
WHERE
    rnk = 1
    AND partnership_balls != 0.0
LIMIT 5;
````

**_Results_**
| Match_ID | Series_Name                                                         | team        | runs_scored | balls_faced |
|----------|---------------------------------------------------------------------|-------------|-------------|-------------|
| 64608    | West Indies tour of South Africa  - 1998 (1998/99)                  | West Indies | 47.0        | 81.0        |
| 64729    | England tour of Zimbabwe  - 2001 (2001/02)                          | England     | 112.0       | 145.0       |
| 64835    | Bangladesh tour of Pakistan  - 2003 (2003)                          | Bangladesh  | 95.0        | 122.0       |
| 65225    | ICC World Cup in England/Ireland/Netherlands/Scotland - 1999 (1999) | New Zealand | 58.0        | 56.0        |
| 65270    | ICC World Cup in Kenya/South Africa/Zimbabwe - 2003 (2002/03)       | New Zealand | 83.0        | 58.0        |


❗ **Insight-** In order to find matches which had the highest batting partnership in a series, we do the ranking based on partnership_runs and partnership_balls. Also, we remove the records that don’t have proper series name.
