


# SQL Zoo 
www.sqlzoo.net

## SUM and COUNT

### 1 Total World Population

    SELECT SUM(population)
    FROM WORLD

### 2 List of Continents

    SELECT DISTINCT(continent)
    FROM world
   
   

### 3 GDP of Africa

    SELECT SUM(gdp) 
    FROM world 
    WHERE continent = 'Africa'
### 4 Count the big countries

    SELECT COUNT(name) 
    FROM world 
    WHERE area > 1000000
### 5 Baltic states population

    SELECT SUM(population) 
    FROM world 
    WHERE name in ('Estonia', 'Latvia', 'Lithuania')
### 6 Counting the countries of each continent

    SELECT continent, COUNT(name) 
    FROM world 
    GROUP BY continent
### 7 Counting big countries in each continent

    SELECT continent, COUNT(name) 
    FROM world 
    WHERE population >= 10000000 
    GROUP BY continent 
### 8 Counting big continents

    SELECT continent 
    FROM world 
    GROUP BY continent 
    HAVING SUM(population) > 100000000

