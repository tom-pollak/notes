# Exam
*Tom Pollak*

## 1.

### (i) **TODO**  

### (ii)

	(a) Recursive
	(b) Doctor has a car parking space
	(c) (1,1) Ward admits (0, M) patients
	(d)
		(i) No as PKs may not be NULL values
		(ii) No, as not every patient may have a telephone no and a PK may not consist of NULL values
	(e) Many doctors may treat many patients
		(f) Requires a separate table where both patientNo and doctorNo are mapped into new table as foreign PKs

  

## 2.

  

(i)

| studentName | module | course           |
| ----------- | ------ | ---------------- |
| T. Pollak   | SYS1   | Computer Science |
| T. Pollak   | THE3   | Computer Science |

1. Updating studentName if student is taking more than one module then needs to be updated for every module
2. Changing course means updating all courses and changing module columns **TODO**

(ii)

	(a) roomNo, moduleCode
	(b) roomNo, moduleCode, roomName, roomLoc
	(c) 1NF, not every attribute determined by every PK part, e.g. roomCapacity is not determined by moduleCode
	(d)
	
| Room           |     | Module         |
| -------------- | --- | -------------- |
| *roomNo*       |     | *moduleCode*   |
| day            |     | moduleStudents |
| time           |     |                |
| moduleCode: FK |     |                |
| roomCapacity   |     |                |
| roomName       |     |                |
| roomLoc        |     |                |

	(e) It not in 3NF as it still has transitive dependancies, e.g. moduleNo is functionally dependant on day and time aswell as roomNo
	(f)

| Room         |     | Module         |     | Lecture          |
| ------------ | --- | -------------- | --- | ---------------- |
| *roomNo*     |     | *moduleCode*   |     | *moduleCode*: FK |
| roomName     |     | moduleStudents |     | *day*            |
| roomLoc      |     |                |     | *time*           |
| roomCapacity |     |                |     | roomNo: FK       |

## 3.

	(i) SELECT * FROM tennis_emma
	    WHERE friends >= 500 AND friends < 1000;
		
	(ii) SELECT tweetID, tweet, reTweets FROM tennis_emma
		 WHERE reTweets = (SELECT min(reTweets) FROM tennis_emma)
		 
	(iii) SELECT count(tweetID) as numMinReTweets, reTweets FROM tennis_emma
		  WHERE reTweets = (SELECT min(reTweets) FROM tennis_emma)
		  
	(iv)
	WITH split(word, str) AS (
		SELECT '', tweet||',' FROM tennis_emma
		UNION ALL 
		SELECT substr(str, 0, instr(str, ' ')), substr(str, instr(str, ' ')+1)
		FROM split WHERE str!=''
	)
	SELECT A.word as word1, B.word as word2
	FROM
		(SELECT word from split
		WHERE word != ''
		GROUP BY word
		HAVING count(*) > 15) A
	CROSS JOIN
		(SELECT word from split
		WHERE word != ''
		GROUP BY word
		HAVING count(*) > 15) B
	ON word1 >= word2
	WHERE word1 != '' and word2 != '' and word1 <> word2 and
		EXISTS (
			SELECT tweet FROM tennis_emma 
			WHERE INSTR( tweet, word1 ) > 0 and INSTR( tweet, word2 ) = 0
		)
		
	(v) SELECT DISTINCT realName, friends, followers FROM tennis_emma
		WHERE friends > (
	    	SELECT avg(friends) FROM tennis_emma 
			WHERE instr(location, 'France') and userTweets > 20000
		)
		
	(vi) SELECT linkURL, count(linkURL) as numLinks FROM tennis_emma
	     WHERE linkURL IS NOT NULL
		 GROUP BY linkURL
		 ORDER BY numLinks DESC
		 LIMIT 1
			   
	     Emma Raducanu: British tennis star makes history and wins US Open
	     http://news.sky.com/story/emma-raducanu-british-tennis-star-makes-history-and-wins-us-open-12405558
		 
	(vii) CREATE TABLE No_Retweet AS
		  SELECT tweetID, tweet, screenName, realName
		  FROM tennis_emma
		  WHERE instr(tweet, 'RT') = 0;
				
		  Number of tweets: 20357
		  
	(viii) SELECT screenName, count(screenName) as numTweets FROM No_Retweet
		   GROUP BY screenName
		   ORDER BY numTweets DESC
	       LIMIT 3