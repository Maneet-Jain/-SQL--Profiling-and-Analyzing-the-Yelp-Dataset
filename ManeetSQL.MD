Data Scientist Role Play: Profiling and Analyzing the Yelp Dataset Coursera Worksheet

This is a 2-part assignment. In the first part, you are asked a series of questions that will help you profile and understand the data just like a data scientist would. For this first part of the assignment, you will be assessed both on the correctness of your findings, as well as the code you used to arrive at your answer. You will be graded on how easy your code is to read, so remember to use proper formatting and comments where necessary.

In the second part of the assignment, you are asked to come up with your own inferences and analysis of the data for a particular research question you want to answer. You will be required to prepare the dataset for the analysis you choose to do. As with the first part, you will be graded, in part, on how easy your code is to read, so use proper formatting and comments to illustrate and communicate your intent as required.

For both parts of this assignment, use this "worksheet." It provides all the questions you are being asked, and your job will be to transfer your answers and SQL coding where indicated into this worksheet so that your peers can review your work. You should be able to use any Text Editor (Windows Notepad, Apple TextEdit, Notepad ++, Sublime Text, etc.) to copy and paste your answers. If you are going to use Word or some other page layout application, just be careful to make sure your answers and code are lined appropriately.
In this case, you may want to save as a PDF to ensure your formatting remains intact for you reviewer.



Part 1: Yelp Dataset Profiling and Understanding

1. Profile the data by finding the total number of records for each of the tables below:

/*
Code used for these calculations is:
SELECT count(*) FROM _____
*/
	
i. Attribute table = 10000
ii. Business table = 10000
iii. Category table = 10000
iv. Checkin table = 10000
v. elite_years table = 10000
vi. friend table = 10000
vii. hours table = 10000
viii. photo table = 10000
ix. review table = 10000
x. tip table = 10000
xi. user table = 10000
	


2. Find the total distinct records by either the foreign key or primary key for each table. If two foreign keys are listed in the table, please specify which foreign key.

/*
Code used for these calculations is:
SELECT COUNT(_____) FROM _____
*/

i. Business = 10000 (id)
ii. Hours = 1562 (business_id)
iii. Category = 2643 (business_id)
iv. Attribute = 1115 (business_id)
v. Review = 10000 (id)
vi. Checkin = 493 (business_id)
vii. Photo = 10000 (id)
viii. Tip = 537 (user_id)
ix. User = 10000 (id)
x. Friend = 11 (user_id)
xi. Elite_years = 2780 (user_id)

Note: Primary Keys are denoted in the ER-Diagram with a yellow key icon.	



3. Are there any columns with null values in the Users table? Indicate "yes," or "no."

	Answer:
	
	No, there are no columns in User table with null value.
	
	
	SQL code used to arrive at answer:

```sql	
	SELECT * FROM user
	WHERE id IS NULL
	OR name IS NULL
	OR review_count IS NULL
	OR yelping_since IS NULL
	OR useful IS NULL
	OR funny IS NULL
	OR cool IS NULL
	OR fans IS NULL
	OR average_stars IS NULL
	OR compliment_hot IS NULL
	OR compliment_more IS NULL
	OR compliment_profile IS NULL
	OR compliment_cute IS NULL
	OR compliment_list IS NULL
	OR compliment_note IS NULL
	OR compliment_plain IS NULL
	OR compliment_cool IS NULL
	OR compliment_funny IS NULL
	OR compliment_writer IS NULL
	OR compliment_photos IS NULL

```	

	
4. For each table and column listed below, display the smallest (minimum), largest (maximum), and average (mean) value for the following fields:

/*
Code used for these calculations is:
SELECT MIN(_____), MAX(_____), AVG(_____) FROM _____
*/

	i. Table: Review, Column: Stars
	
		min: 1		max: 5		avg: 3.7082
		
	
	ii. Table: Business, Column: Stars
	
		min: 1.0		max: 5.0		avg: 3.6549
		
	
	iii. Table: Tip, Column: Likes
	
		min: 0		max: 2		avg: 0.0144
		
	
	iv. Table: Checkin, Column: Count
	
		min: 1		max: 53		avg: 1.9414
		
	
	v. Table: User, Column: Review_count
	
		min: 0		max: 2000	avg: 24.2995
		


5. List the cities with the most reviews in descending order:

	SQL code used to arrive at answer:
	
	SELECT SUM(review_count) AS Total, city
	FROM business
	GROUP BY city 
	ORDER BY Total DESC
	
	
	Copy and Paste the Result Below:

	+-------+-----------------+
	| Total     | city                       |
	+-------+-----------------+
	| 82854   | Las Vegas       	 |
	| 34503   | Phoenix         	 |
	| 24113   | Toronto         	 |
	| 20614   | Scottsdale      	 |
	| 12523   | Charlotte       	 |
	| 10871   | Henderson       	 |
	| 10504   | Tempe           	 |
	|  9798    | Pittsburgh      	 |
	|  9448    | Montréal        	 |
	|  8112    | Chandler        	 |
	|  6875    | Mesa            	 |
	|  6380    | Gilbert         	 |
	|  5593    | Cleveland       	 |
	|  5265    | Madison         	 |
	|  4406    | Glendale        	 |
	|  3814    | Mississauga     	 |
	|  2792    | Edinburgh       	 |
	|  2624    | Peoria          	 |
	|  2438    | North Las Vegas 	 |
	|  2352    | Markham         	 |
	|  2029    | Champaign       	 |
	|  1849    | Stuttgart       	 |
	|  1520    | Surprise        	 |
	|  1465    | Lakewood        	 |
	|  1155    | Goodyear        	 |
	+-------+-----------------+
	(Output limit exceeded, 25 of 362 total rows shown)	
	

	
6. Find the distribution of star ratings to the business in the following cities:

i. Avon

SQL code used to arrive at answer:

SELECT SUM(review_count) AS Numbers, stars
FROM business
WHERE city = "Avon"
GROUP BY stars


Copy and Paste the Resulting Table Below (2 columns – star rating and count):

+---------+-------+
| Numbers  | stars 	  |	
+---------+-------+
|      10       |   1.5 	  |
|       6 	   |   2.5 	  |
|      88 	   |   3.5 	  |
|      21 	   |   4.0 	  |
|      31 	   |   4.5 	  |
|       3 	   |   5.0 	  |
+---------+-------+



ii. Beachwood

SQL code used to arrive at answer:

SELECT SUM(review_count) AS Numbers, stars
FROM business
WHERE city = "Beachwood"
GROUP BY stars


Copy and Paste the Resulting Table Below (2 columns – star rating and count):

+---------+-------+
| Numbers  | stars     |
+---------+-------+
|       8 	   |   2.0  	  |
|       3 	   |   2.5 	  |
|      11 	   |   3.0     |
|       6 	   |   3.5 	  |
|      69 	   |   4.0 	  |
|      17 	   |   4.5 	  |
|      23 	   |   5.0 	  |
+---------+-------+

		


7. Find the top 3 users based on their total number of reviews:
		
	SQL code used to arrive at answer:

	SELECT review_count, name
	FROM user
	ORDER BY review_count DESC
	LIMIT 3
	
		
	Copy and Paste the Result Below:

	+--------------+--------+
	| review_count    | name      |
	+--------------+--------+
	|         2000        | Gerald    |
	|         1629        | Sara        |
	|         1339        | Yuri        |
	+--------------+--------+

		


8. Does posing more reviews correlate with more fans?

	Please explain your findings and interpretation of the results:

	Code Used:

	SELECT review_count, fans, name
	FROM user
	ORDER BY fans DESC
	LIMIT 1

	Output:

	+--------------+------+------+
	| review_count    | Fans    | name  |
	+--------------+------+------+
	|          609         |  503    | Amy    |
	+--------------+------+------+

	Code Used:

	SELECT review_count, fans, name
	FROM user
	ORDER BY review_count DESC
	LIMIT 1

	Output:

	+--------------+------+-----------+
	| review_count    | fans    | name           |
	+--------------+------+-----------+
	|         2000        |  253    | Gerald         |
	+--------------+------+-----------+

As we can see that Amy has the most fans which is 503 but has the review count of only 609 whereas the most review count record is held by Gerald.
Hence, this clearly contradicts the direct relationship between fans and review count.

	

9. Are there more reviews with the word "love" or with the word "hate" in them?

	Answer:

	Reviews with the word "love"(1780) are more than reviews with the word "hate"(232)

	
	SQL code used to arrive at answer:

	SELECT COUNT(*), "Love" AS Output
	FROM review
	WHERE text LIKE "%love%"
	/* Using %___% as a  placeholder to count reviews that has word Love in it */
	UNION
	/* Counting reviews with word Love and Hate individually and then using UNION to combine the results*/
	SELECT COUNT(*), "Hate" AS Output
	FROM review
	WHERE text LIKE "%hate%"


	
	
10. Find the top 10 users with the most fans:

	SQL code used to arrive at answer:

	SELECT fans, name
	FROM user
	ORDER BY fans DESC
	LIMIT 10

	
	Copy and Paste the Result Below:

	+------+-----------+
	| fans    | name      	    |
	+------+-----------+
	|  503    | Amy       	    |
	|  497    | Mimi      	    | 
	|  311    | Harald    	    |
	|  253    | Gerald    	    |
	|  173    | Christine     |
	|  159    | Lisa      	    |
	|  133    | Cat       	    |
	|  126    | William   	    |
	|  124    | Fran    	    |
	|  120    | Lissa           |
	+------+-----------+


	
		

Part 2: Inferences and Analysis

1. Pick one city and category of your choice and group the businesses in that city or category by their overall star rating. Compare the businesses with 2-3 stars to the businesses with 4-5 stars and answer the following questions. Include your code.

	
i. Do the two groups you chose to analyze have a different distribution of hours?

Both the groups follow similar timeline on Saturday. Almost all of them opens till late night.


ii. Do the two groups you chose to analyze have a different number of reviews?

Group 2(206) that is stars 4-5 have more reviews then the group 1(89) with 2-3 stars.
         
         
iii. Are you able to infer anything from the location data provided between these two groups? Explain.

Not really. They have different locations.

SQL code used for analysis:

SELECT name, city,  address, stars, review_count AS Reviews, hours, category
FROM business AS b LEFT JOIN hours AS h ON b.id = h.business_id
/* Left Join because we want the list of all the restaurants*/
/* Naming business table as 'b', hours table as 'h' and category table as 'c' */
INNER JOIN category  AS c ON b.id = c.business_id
WHERE city = "Toronto" AND category = "Restaurants"
GROUP BY name
ORDER BY stars

		
		
2. Group business based on the ones that are open and the ones that are closed. What differences can you find between the ones that are still open and the ones that are closed? List at least two differences and the SQL code you used to arrive at your answer.
		
i. Difference 1:

Businesses that are still open have more reviews on average than the ones that are closed.        
         
ii. Difference 2:

There are more business that are still open and listed as “useful” or “funny”.         
         
         
SQL code used for analysis:

SELECT AVG(b.stars), SUM(b.review_count), AVG(b.review_count), COUNT(r.useful)+COUNT(r.funny), is_open
/* AVG function is used to calculate the average, SUM function is used to calculate the summation and COUNT function is used to count the number of items*/
FROM business b INNER JOIN review r ON b.id = r.id
/* Naming business table as 'b' and review table as 'r' */
GROUP BY b.is_open
 /* Grouping the results by the open or closed status of the business*/
	
	
3. For this last part of your analysis, you are going to choose the type of analysis you want to conduct on the Yelp dataset and are going to prepare the data for analysis.

Ideas for analysis include: Parsing out keywords and business attributes for sentiment analysis, clustering businesses to find commonalities or anomalies between them, predicting the overall star rating for a business, predicting the number of fans a user will have, and so on. These are just a few examples to get you started, so feel free to be creative and come up with your own problem you want to solve. Provide answers, in-line, to all of the following:
	
i. Indicate the type of analysis you chose to do:

Here I chose to study the preference among different types of Restaurants on yelp.
         
         
ii. Write 1-2 brief paragraphs on the type of data you will need for your analysis and why you chose that data:

I will pick several types of Eating places like "Food", "Restaurants", "Fast Food", "Cafe", "Pubs".
Then I will analyze their average star ratings and number of reviews so that I can get some insights on which type of food is popular on yelp.

                           
                  
iii. Output of your finished dataset:

+-------------+----------------------+---------------+-------------------+-------------+
| category         | Number_Of_Businesses   |    AVG(stars)       | AVG(review_count)     | city                |
+-------------+----------------------+---------------+-------------------+-------------+
| Food               |                   97 	     | 3.75773195876  |     101.845360825     | Middleton       |
| Restaurants    |                  289 	     | 3.53979238754  |     87.0034602076     | Chesterland    |
| Pubs               |                   34	     | 3.38235294118  |     45.2647058824     | Toronto          |
| Fast Food       |                   34	     | 3.19117647059  |     35.2058823529     | Charlotte        |
+-------------+----------------------+---------------+-------------------+-------------+
         
         
iv. Provide the SQL code you used to create your final dataset:

SELECT c.category, COUNT(b.name) AS Number_Of_Businesses, AVG(stars), AVG(review_count), b.city
/* AVG function is used to calculate the average and COUNT function is used to count the number of items*/
FROM business b INNER JOIN hours h ON b.id = h.business_id
/* Naming business table as 'b', hours table as 'h' and category table as 'c' */
INNER JOIN category c ON c.business_id = b.id
WHERE c.category IN ("Food","Restaurants","Fast Food","Cafe","Pubs")
/* Only looking for categories named as Food, Restaurants, Fast Food, Cafe, Pubs */
GROUP BY c.category
ORDER BY AVG(stars) DESC
/* Ordering the result by average of stars in descending order*/
