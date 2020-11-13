


## SQL zoo
### The JOIN operation

#### 1

    SELECT matchid, player 
    FROM goal 
    WHERE teamid = 'GER'
#### 2

    SELECT id,stadium,team1,team2 
    FROM game 
    WHERE id = 1012
#### 3

    SELECT team1, team2, player
    FROM game JOIN goal ON (game.id = goal.matchid) 
    WHERE player LIKE 'Mario%'
#### 4

    SELECT team1, team2, player
    FROM game JOIN goal ON (game.id = goal.matchid) 
    WHERE player LIKE 'Mario%'
#### 5

    SELECT player, teamid, coach, gtime
    FROM goal JOIN eteam ON (goal.teamid = eteam.id )
    WHERE gtime<=10
#### 6

    SELECT mdate, teamname 
    FROM game JOIN eteam ON (team1 = eteam.id) 
    WHERE coach = 'Fernando Santos'
#### 7

    SELECT player 
    FROM goal JOIN game ON (game.id = goal.matchid)   
    WHERE stadium = 'National Stadium, Warsaw'
#### 8

    SELECT DISTINCT(player)
    FROM game JOIN goal ON matchid = id 
    WHERE ((team1='GER' OR team2='GER') 
    AND goal.teamid <> 'GER')
#### 9

    SELECT teamname, COUNT(teamname) 
    FROM eteam JOIN goal ON eteam.id=goal.teamid 
    GROUP BY teamname
#### 10

    SELECT stadium, COUNT(gtime)  
    FROM game JOIN goal ON game.id = goal.matchid 
    GROUP BY stadium
#### 11

    SELECT goal.matchid,game.mdate, COUNT(matchid)
    FROM game JOIN goal ON goal.matchid = game.id 
    WHERE (game.team1 = 'POL' OR game.team2 = 'POL')
    GROUP BY game.mdate, goal.matchid
    ORDER BY goal.matchid 
#### 12

    SELECT matchid, mdate, COUNT(gtime) 
    FROM game JOIN goal ON goal.matchid = game.id
    WHERE (teamid = 'GER')
    GROUP BY matchid, mdate
#### 13

    
    SELECT
    
    mdate,
    team1,
    
    SUM(
    CASE 
    WHEN teamid = team1
    THEN 1
    ELSE 0
    END) AS score1,
    
    team2,
    
    SUM(
    CASE 
    WHEN teamid = team2
    THEN 1
    ELSE 0
    END) AS score2
    
    FROM game LEFT JOIN goal 
    ON (goal.matchid = game.id)
    GROUP BY mdate, team1, team2
    ORDER BY mdate, matchid, team1, team2

