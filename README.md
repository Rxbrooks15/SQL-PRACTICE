# SQL-PRACTICE
ADVANCED SELECT 
Query an alphabetically ordered list of all names in OCCUPATIONS, immediately followed by the first letter of each profession as a parenthetical (i.e.: enclosed in parentheses). For example: AnActorName(A), ADoctorName(D), AProfessorName(P), and ASingerName(S).
Query the number of ocurrences of each occupation in OCCUPATIONS

ALTER TABLE OCCUPATIONS ADD Letter VARCHAR(100);

UPDATE OCCUPATIONS
SET Letter = CASE 
    WHEN Occupation = 'Doctor' THEN 'D'
    WHEN Occupation = 'Singer' THEN 'S'
    WHEN Occupation = 'Actor' THEN 'A'
    WHEN Occupation = 'Professor' THEN 'P'
    ELSE NULL
END;
SELECT 
    CONCAT(Name, '(', Letter, ')') AS FormattedName
FROM 
    OCCUPATIONS
ORDER BY 
    Name;


SELECT 
    CONCAT('There are a total of ', COUNT(*), ' ', LOWER(Occupation), 's.') AS Result

FROM 
    OCCUPATIONS
GROUP BY 
    Occupation
ORDER BY 
    COUNT(*), LOWER(Occupation);

OUTPUT:
Aamina(D) 
Ashley(P) 
Belvet(P) 
Britney(P) 
Christeen(S) 
Eve(A) 
Jane(S) 
Jennifer(A) 
Jenny(S) 
Julia(D) 
Ketty(A) 
Kristeen(S) 
Maria(P) 
Meera(P) 
Naomi(P) 
Priya(D) 
Priyanka(P) 
Samantha(A) 
There are a total of 3 doctors. 
There are a total of 4 actors. 
There are a total of 4 singers. 
There are a total of 7 professors.
