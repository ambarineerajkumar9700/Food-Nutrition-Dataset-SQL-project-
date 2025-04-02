# Food-Nutrition-Dataset-SQL-project-
# Project overview

📌 Project Name: Food Nutrition analysis

📌 Dateset Name:Food Nutrition Dataset 
# ![dataset-cover](https://github.com/user-attachments/assets/e5a24863-7dfc-46c1-8234-60d88193a4fa)



# Introduction
The Food Nutrition Database project aims to store and analyze the nutritional composition of various food items using Oracle SQL. The dataset includes attributes such as calories, fats, proteins, vitamins, minerals, and food type classifications. This database serves as a valuable resource for health applications, dietary tracking, and nutritional research.

#  Objectives

🔹 Organize nutritional data efficiently in a structured format.

🔹 Enable fast querying for diet planning and health tracking.

🔹 Support research on food nutrition and dietary habits.

🔹 Provide insights into healthier eating patterns.
Certainly! Here is the converted SQL code wrapped in Markdown code blocks for GitHub:

```sql
# Create Dataset As NutritionalFacts_Fruit_Vegetables_Seafood dataset

CREATE TABLE food_nutrition (
    food_name VARCHAR2(255),
    calories NUMBER,
    calories_from_fat NUMBER,
    total_fat NUMBER,
    total_fat_percentage NUMBER,
    sodium NUMBER,
    sodium_percentage NUMBER,
    potassium NUMBER,
    potassium_percentage NUMBER,
    total_carbohydrate NUMBER,
    total_carbohydrate_percentage NUMBER,
    dietary_fiber NUMBER,
    dietary_fiber_percentage NUMBER,
    sugars NUMBER,
    protein NUMBER,
    vitamin_a NUMBER,
    vitamin_c NUMBER,
    calcium NUMBER,
    iron NUMBER,
    saturated_fat NUMBER,
    saturated_fat_percentage NUMBER,
    cholesterol NUMBER,
    cholesterol_percentage NUMBER,
    food_type VARCHAR2(100)
);

-- 1. Retrieve the food items with the highest calorie content per serving
SELECT foodandserving, calories FROM cp
WHERE calories = (SELECT MAX(calories) FROM cp);

-- 2. Find the total number of unique food types in the dataset
SELECT COUNT(DISTINCT sugars) AS sugars FROM cp;

-- 3. Calculate the average sodium content per serving for all food items
SELECT AVG(sodium1) AS sodium1 FROM cp;

-- 4. List the food items that have more than 20% of the daily recommended value for saturated fat
SELECT foodandserving, saturatedfat2 FROM cp
WHERE saturatedfat2 > 20;

-- 5. Retrieve the top 10 food items with the highest protein content
SELECT foodandserving, protein FROM cp
WHERE protein >= (SELECT MIN(protein) FROM (SELECT protein FROM cp ORDER BY protein DESC FETCH FIRST 10 ROWS ONLY));

-- 6. Find the food items with the highest potassium content per serving among those with more than 10g of total carbohydrates
SELECT foodandserving, potassium, TOTALCARBOHYDRATE2 FROM cp
WHERE TOTALCARBOHYDRATE2 > 10
ORDER BY potassium DESC;

-- 7. Calculate the total number of calories in the dataset and the percentage of calories contributed by sugars
SELECT SUM(calories) AS total_calories, SUM(sugars) AS sugar_calories_percentage FROM cp;

-- 8. List the food items with more than 5g of dietary fibre and order them by their fibre content
SELECT foodandserving, dietaryfiber FROM cp
WHERE dietaryfiber > 5 ORDER BY dietaryfiber DESC;

-- 9. Retrieve the food items where the calories from fat are more than 30% of the total calories
SELECT calories_from_fat, calories FROM cp
WHERE calories > 0.3;

-- 10. Calculate the average percentage of daily recommended vitamin A for all food items
SELECT AVG(vitaminA) AS average_vitaminA FROM cp;

-- 11. Find the food items with the highest calcium content per serving among those classified as a certain food type
SELECT foodandserving, calcium FROM cp
WHERE FOODTYPE = FOODTYPE
ORDER BY calcium DESC FETCH FIRST 1 ROWS ONLY;

-- 12. List the top 5 food types with the highest average sodium content per serving
SELECT foodandserving, AVG(sodium1) AS average_sodium1 FROM cp
GROUP BY foodandserving
ORDER BY average_sodium1 DESC FETCH FIRST 5 ROWS ONLY;

-- 13. Calculate the total number of food items in each food type and order them by the count
SELECT foodtype, COUNT(*) AS total_fooditems FROM cp
GROUP BY foodtype
ORDER BY total_fooditems DESC;

-- 14. Retrieve the food items where the ratio of calories to protein is the highest
SELECT foodandserving, calories, protein, (calories / protein) AS calories_to_protein_ratio
FROM cp
WHERE protein != 0
ORDER BY calories_to_protein_ratio DESC FETCH FIRST 1 ROWS ONLY;

-- 15. Find the food items with the lowest ratio of calories to total carbohydrates among those with less than 10g of sugar
SELECT foodandserving, calories, TOTALCARBOHYDRATE2, sugars, (calories / TOTALCARBOHYDRATE2) AS calories_to_carbs_ratio
FROM cp
WHERE sugars < 10
ORDER BY calories_to_carbs_ratio ASC FETCH FIRST 1 ROWS ONLY;
```


# Report

✅ Structured Schema – Contains nutritional details like calories, fat, protein, vitamins, and minerals.

✅ Categorized Data – Foods are classified into types (e.g., Meat, Vegetables, Fruits, Grains, Fish).

✅ Efficient Querying – Users can filter and analyze data based on nutritional values.

✅ Scalability – The dataset can be expanded with more food items and additional attributes.

# Conclusion

The Food Nutrition Database is a comprehensive, structured, and scalable solution for storing and analyzing food-related nutritional data. It provides a foundation for diet tracking applications, health monitoring systems, and research studies. By integrating with machine learning models, this database can further enhance predictive analysis of dietary trends.
