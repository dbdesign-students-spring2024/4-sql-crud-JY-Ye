.mode csv
.import restaurants.csv restaurants

#Find all cheap restaurants in a particular neighborhood:

SELECT * FROM restaurants
WHERE price_tier = 'cheap' AND neighborhood = 'ExampleNeighborhood';

#Find all restaurants in a particular genre with 3 stars or more:

SELECT * FROM restaurants
WHERE category = 'ExampleGenre' AND average_rating >= 3
ORDER BY average_rating DESC;

#Find all restaurants that are open now:

SELECT * FROM restaurants
WHERE substr(opening_hours, 1, 5) <= '15:00' AND substr(opening_hours, 7, 5) >= '15:00';

#Leave a review for a restaurant

INSERT INTO reviews (restaurant_id, review_text, rating, created_at)
VALUES (1, 'Great food and service!', 5, 'YYYY-MM-DD HH:MM:SS');

#Delete all restaurants that are not good for kids:

DELETE FROM restaurants
WHERE good_for_kids = FALSE;

#Find the number of restaurants in each NYC neighborhood:

SELECT neighborhood, COUNT(*) AS number_of_restaurants
FROM restaurants
GROUP BY neighborhood;