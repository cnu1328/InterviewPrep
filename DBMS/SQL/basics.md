# SQL Database Setup and Operations

## 1. Create a New Database

```sql
-- Create a new database named shapefit
CREATE DATABASE shapefit;
```

**Description**: This command creates a new database named `shapefit`.

## 2. Use the Database

```sql
-- Select the shapefit database to use
USE shapefit;
```

**Description**: This command selects the `shapefit` database as the current database to work on.

![FoodItems](https://github.com/cnu1328/InterviewPrep/assets/110097436/d4438fcc-8d75-437c-9c07-894697fbf591)

## 3. Create the `food` Table

```sql
-- Create a table named food with the specified columns and data types
CREATE TABLE food (
    foodId VARCHAR(255) PRIMARY KEY,
    foodName VARCHAR(255),
    calories INT,
    proteins INT,
    carbs INT,
    fats INT,
    quantity DOUBLE,
    unit VARCHAR(255)
);
```

**Description**: This command creates a table named `food` with columns for food ID, name, calories, proteins, carbs, fats, quantity, and unit of measurement. The `foodId` column is designated as the primary key.

#### 4. Insert Data into the `food` Table

```sql
-- Insert data into the food table
INSERT INTO food (foodId, foodName, calories, proteins, carbs, fats, quantity, unit) VALUES
("1", "srinu", 10, 20, 30, 40, 5, "grams"),
("12", "srinu", 10, 20, 30, 40, 5, "grams");
```

**Description**: This command inserts two records into the `food` table.

#### 5. Select All Data from the `food` Table

```sql
-- Retrieve all records from the food table
SELECT * FROM food;
```

**Description**: This command retrieves all records from the `food` table.

#### 6. Update a Particular Field in the `food` Table

```sql
-- Update the foodName field of the record with foodId "1"
UPDATE food SET foodName = "Hero" WHERE foodId = "1";

-- Retrieve all records from the food table to verify the update
SELECT * FROM food;
```

**Description**: This command updates the `foodName` of the record with `foodId` "1" to "Hero". The subsequent `SELECT` statement retrieves all records to verify the update.

#### 7. Delete a Food Item from the `food` Table

```sql
-- Delete the record with foodId "1" from the food table
DELETE FROM food WHERE foodId = "1";

-- Retrieve all records from the food table to verify the deletion
SELECT * FROM food;
```

**Description**: This command deletes the record with `foodId` "1" from the `food` table. The subsequent `SELECT` statement retrieves all records to verify the deletion.

### Summary

- **Database Creation**: `CREATE DATABASE shapefit;`
- **Database Selection**: `USE shapefit;`
- **Table Creation**: `CREATE TABLE food (...)`
- **Data Insertion**: `INSERT INTO food VALUES (...)`
- **Data Retrieval**: `SELECT * FROM food;`
- **Data Update**: `UPDATE food SET ... WHERE ...;`
- **Data Deletion**: `DELETE FROM food WHERE ...;`

## Create the `DietPlan`

![Screenshot (62)](https://github.com/cnu1328/InterviewPrep/assets/110097436/cb19a211-9584-4fdc-8e15-85830f7299f4)

Sure, here are the SQL commands written in a structured way:

### Creating Tables

#### `dietplan` Table

```sql
CREATE TABLE dietplan (
    dietPlanId VARCHAR(255) PRIMARY KEY,
    dietPlanName VARCHAR(255),
    targetCalories INT,
    targetProteins INT,
    targetCarbs INT,
    targetFats INT
);
```

#### `dietplan-food` Table

```sql
CREATE TABLE dietplan_food (
    dietPlanId VARCHAR(255),
    mealTime VARCHAR(255),
    foodId VARCHAR(255),
    foodName VARCHAR(255),
    calories INT,
    proteins INT,
    fats INT,
    carbs INT,
    measurement VARCHAR(255),
    PRIMARY KEY (dietPlanId, mealTime, foodId),
    FOREIGN KEY (dietPlanId) REFERENCES dietplan(dietPlanId),
    FOREIGN KEY (foodId) REFERENCES food(foodId)
);
```

### Inserting Data

#### Insert into `dietplan`

```sql
INSERT INTO dietplan (dietPlanId, dietPlanName, targetCalories, targetProteins, targetCarbs, targetFats)
VALUES ("1", "WeightLoss", 100, 100, 100, 100);
```

#### Insert into `dietplan_food`

```sql
INSERT INTO dietplan_food (dietPlanId, mealTime, foodId, foodName, calories, proteins, fats, carbs, measurement)
VALUES ("1", "Breakfast", "12", "Mango", 10, 10, 10, 10, "Grams");
```

### Retrieving Data

#### Select all from `dietplan`

```sql
SELECT * FROM dietplan;
```

### Updating Data

#### Update a `dietplan`

```sql
UPDATE dietplan
SET dietPlanName = 'NewWeightLoss', targetCalories = 150, targetProteins = 150, targetCarbs = 150, targetFats = 150
WHERE dietPlanId = '1';
```

### Deleting Data

#### Delete a `dietplan`

```sql
DELETE FROM dietplan WHERE dietPlanId = '1';
```

### Sample Data

```sql
-- Sample data for diet_plan table
INSERT INTO diet_plan (diet_plan_id, trainer_id, name, description, plan_type, target_calories, target_carbs, target_protein, target_fats, actual_calories, actual_carbs, actual_protein, actual_fats, created_at)
VALUES
('1', 'trainer1', 'Weight Loss Plan', 'A plan focused on weight loss.', 'weight_loss', 2000, 250, 150, 70, 1800, 200, 120, 60, '2024-01-01'),
('2', 'trainer2', 'Muscle Gain Plan', 'A plan focused on muscle gain.', 'muscle_gain', 3000, 300, 200, 100, 3100, 320, 210, 110, '2024-01-05');

-- Sample data for food table
INSERT INTO food (food_id, food_name, portion, measurement, calories, proteins, carbs, fats)
VALUES
('1', 'Chicken Breast', 100, 'grams', 165, 31, 0, 3.6),
('2', 'Brown Rice', 100, 'grams', 110, 2.6, 23, 0.9),
('3', 'Broccoli', 100, 'grams', 55, 3.7, 11.2, 0.6);

-- Sample data for diet_plan_food table
INSERT INTO diet_plan_food (diet_plan_id, meal_name, food_id, calories, proteins, carbs, fats, portion, measurement)
VALUES
('1', 'Breakfast', '1', 165, 31, 0, 3.6, 100, 'grams'),
('1', 'Lunch', '2', 110, 2.6, 23, 0.9, 100, 'grams'),
('2', 'Dinner', '3', 55, 3.7, 11.2, 0.6, 100, 'grams');
```

#### Basic Questions

1. **What is a primary key? Why is it important in a table?**

   - A primary key is a unique identifier for a record in a table. It ensures that each record is unique and can be referenced by other tables.

2. **What is a foreign key? How does it help in maintaining relationships between tables?**

   - A foreign key is a field in a table that is a primary key in another table. It helps in maintaining referential integrity between tables by ensuring that the value in the foreign key column matches one in the related table's primary key column.

3. **Write an SQL query to select all columns from the `diet_plan` table.**

   ```sql
   SELECT * FROM diet_plan;
   ```

   | diet_plan_id | trainer_id | name             | description                    | plan_type   | target_calories | target_carbs | target_protein | target_fats | actual_calories | actual_carbs | actual_protein | actual_fats | created_at |
   | ------------ | ---------- | ---------------- | ------------------------------ | ----------- | --------------- | ------------ | -------------- | ----------- | --------------- | ------------ | -------------- | ----------- | ---------- |
   | 1            | trainer1   | Weight Loss Plan | A plan focused on weight loss. | weight_loss | 2000            | 250          | 150            | 70          | 1800            | 200          | 120            | 60          | 2024-01-01 |
   | 2            | trainer2   | Muscle Gain Plan | A plan focused on muscle gain. | muscle_gain | 3000            | 300          | 200            | 100         | 3100            | 320          | 210            | 110         | 2024-01-05 |

4. **Write an SQL query to select all columns from the `food` table.**

   ```sql
   SELECT * FROM food;
   ```

   | food_id | food_name      | portion | measurement | calories | proteins | carbs | fats |
   | ------- | -------------- | ------- | ----------- | -------- | -------- | ----- | ---- |
   | 1       | Chicken Breast | 100     | grams       | 165      | 31       | 0     | 3.6  |
   | 2       | Brown Rice     | 100     | grams       | 110      | 2.6      | 23    | 0.9  |
   | 3       | Broccoli       | 100     | grams       | 55       | 3.7      | 11.2  | 0.6  |

5. **Write an SQL query to find the names of all diet plans.**

   ```sql
   SELECT name FROM diet_plan;
   ```

   | name             |
   | ---------------- |
   | Weight Loss Plan |
   | Muscle Gain Plan |

6. **What are the `not null` constraints? Why are they used?**
   - `NOT NULL` constraints ensure that a column cannot have a NULL value. They are used to enforce that certain fields must always contain a value.

#### Intermediate Questions

7. **Write an SQL query to find all foods with more than 100 calories.**

   ```sql
   SELECT * FROM food WHERE calories > 100;
   ```

   | food_id | food_name      | portion | measurement | calories | proteins | carbs | fats |
   | ------- | -------------- | ------- | ----------- | -------- | -------- | ----- | ---- |
   | 1       | Chicken Breast | 100     | grams       | 165      | 31       | 0     | 3.6  |
   | 2       | Brown Rice     | 100     | grams       | 110      | 2.6      | 23    | 0.9  |

8. **Write an SQL query to find the diet plan names and their corresponding descriptions.**

   ```sql
   SELECT name, description FROM diet_plan;
   ```

   | name             | description                    |
   | ---------------- | ------------------------------ |
   | Weight Loss Plan | A plan focused on weight loss. |
   | Muscle Gain Plan | A plan focused on muscle gain. |

9. **Write an SQL query to find all foods and their nutritional values for a specific diet plan (use `diet_plan_id` as a parameter).**

   ```sql
   SELECT food.*
   FROM food
   JOIN diet_plan_food ON food.food_id = diet_plan_food.food_id
   WHERE diet_plan_food.diet_plan_id = '1';
   ```

   | food_id | food_name      | portion | measurement | calories | proteins | carbs | fats |
   | ------- | -------------- | ------- | ----------- | -------- | -------- | ----- | ---- |
   | 1       | Chicken Breast | 100     | grams       | 165      | 31       | 0     | 3.6  |
   | 2       | Brown Rice     | 100     | grams       | 110      | 2.6      | 23    | 0.9  |

10. **What is an index in a database? How does it help in query performance?**

    - An index is a database object that improves the speed of data retrieval operations on a table. It is created on columns that are frequently used in search conditions or join operations.

11. **Explain the role of the `default` keyword in the `diet_plan_food` table.**

    - The `DEFAULT` keyword is used to set a default value for a column if no value is specified during an insert operation.

12. **Write an SQL query to find the total number of calories in a specific meal of a specific diet plan.**
    ```sql
    SELECT SUM(calories)
    FROM diet_plan_food
    WHERE diet_plan_id = '1' AND meal_name = 'Breakfast';
    ```
    | SUM(calories) |
    | ------------- |
    | 165           |

#### Advanced Questions

13. **Write an SQL query to update the `actual_calories` of a diet plan based on the sum of calories from all associated foods.**

    ```sql
    UPDATE diet_plan
    SET actual_calories = (
        SELECT SUM(calories)
        FROM diet_plan_food
        WHERE diet_plan_food.diet_plan_id = diet_plan.diet_plan_id
    )
    WHERE diet_plan_id = '1';
    ```

    - This query will update the `actual_calories` in the `diet_plan` table for the specified `diet_plan_id` to the sum of the calories from all associated foods.

14. **Write an SQL query to delete a diet plan and all its associated foods.**

    ```sql
    DELETE FROM diet_plan_food WHERE diet_plan_id = '1';
    DELETE FROM diet_plan WHERE diet_plan_id = '1';
    ```

    - This query deletes all entries in `diet_plan_food` associated with the specified `diet_plan_id`, and then deletes the diet plan itself.

15. **Explain how you would enforce referential integrity in the `diet_plan_food` table.**

    - Referential integrity in the `diet_plan_food` table is enforced using foreign key constraints, ensuring that `diet_plan_id` and `food_id` must exist in the `diet_plan` and `food` tables, respectively.

16. **Write an SQL query to find diet plans that have more than a certain number of meals.**

```sql
    SELECT diet_plan_id, COUNT(DISTINCT meal_name) AS meal_count
    FROM diet_plan_food
    GROUP BY diet_plan_id
    HAVING meal_count > 1;

```

| diet_plan_id | meal_count |
| ------------ | ---------- |
| 1            | 2          |

17. **What are the benefits of using `uuid` as a primary key?**

    - Using `uuid` as a primary key provides a unique identifier that is globally unique, reducing the chances of collisions and making it easier to merge data from different sources.

18. **Write an SQL query to find the average nutritional values (calories, proteins, carbs, fats) of all foods in a diet plan.**
    ```sql
    SELECT AVG(calories) AS avg_calories, AVG(proteins) AS avg_proteins, AVG(carbs) AS avg_carbs, AVG(fats) AS avg_fats
    FROM food
    JOIN diet_plan_food ON food.food_id = diet_plan_food.food_id
    WHERE diet_plan_food.diet_plan_id = '1';
    ```
    | avg_calories | avg_proteins | avg_carbs | avg_fats |
    | ------------ | ------------ | --------- | -------- |
    | 137.5        | 16.8         | 11.5      | 2.25     |

#### Comprehensive Questions

19. **Write an SQL query to find diet plans where the actual nutritional values exceed the target values.**

    ```sql
    SELECT *
    FROM diet_plan
    WHERE actual_calories > target_calories
      AND actual_carbs > target_carbs
      AND actual_protein > target_protein
      AND actual_fats > target_fats;
    ```

    | diet_plan_id | trainer_id | name             | description                    | plan_type   | target_calories | target_carbs | target_protein | target_fats | actual_calories | actual_carbs | actual_protein | actual_fats | created_at |
    | ------------ | ---------- | ---------------- | ------------------------------ | ----------- | --------------- | ------------ | -------------- | ----------- | --------------- | ------------ | -------------- | ----------- | ---------- |
    | 2            | trainer2   | Muscle Gain Plan | A plan focused on muscle gain. | muscle_gain | 3000            | 300          | 200            | 100         | 3100            | 320          | 210            | 110         | 2024-01-05 |

20. **How would you design a database schema to track user feedback on each diet plan? Outline the tables and relationships.**

    - To track user feedback on each diet plan, you would need to create a `feedback` table:

    ```sql
    CREATE TABLE feedback (
        feedback_id UUID PRIMARY KEY,
        diet_plan_id UUID NOT NULL REFERENCES diet_plan(diet_plan_id),
        user_id UUID NOT NULL,
        feedback_text TEXT,
        rating INT CHECK (rating >= 1 AND rating <= 5),
        created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
    );
    ```

21. **Write an SQL query to generate a summary report of all diet plans, including the total target and actual nutritional values.**

    ```sql
    SELECT name,
           SUM(target_calories) AS total_target_calories,
           SUM(actual_calories) AS total_actual_calories,
           SUM(target_carbs) AS total_target_carbs,
           SUM(actual_carbs) AS total_actual_carbs,
           SUM(target_protein) AS total_target_protein,
           SUM(actual_protein) AS total_actual_protein,
           SUM(target_fats) AS total_target_fats,
           SUM(actual_fats) AS total_actual_fats
    FROM diet_plan
    GROUP BY name;
    ```

    | name             | total_target_calories | total_actual_calories | total_target_carbs | total_actual_carbs | total_target_protein | total_actual_protein | total_target_fats | total_actual_fats |
    | ---------------- | --------------------- | --------------------- | ------------------ | ------------------ | -------------------- | -------------------- | ----------------- | ----------------- |
    | Weight Loss Plan | 2000                  | 1800                  | 250                | 200                | 150                  | 120                  | 70                | 60                |
    | Muscle Gain Plan | 3000                  | 3100                  | 300                | 320                | 200                  | 210                  | 100               | 110               |

22. **Explain the concept of database normalization and its importance in database design.**

    - Database normalization is the process of organizing a database to reduce redundancy and improve data integrity. It involves dividing large tables into smaller tables and defining relationships between them.

23. **Write an SQL query to copy all foods from one diet plan to another.**

    ```sql
    INSERT INTO diet_plan_food (diet_plan_id, meal_name, food_id, calories, proteins, carbs, fats, portion, measurement)
    SELECT '2', meal_name, food_id, calories, proteins, carbs, fats, portion, measurement
    FROM diet_plan_food
    WHERE diet_plan_id = '1';
    ```

24. **How would you implement a feature to track the history of changes to diet plans? Outline the necessary database schema modifications.**
    - To track the history of changes to diet plans, you could add a `diet_plan_history` table:
    ```sql
    CREATE TABLE diet_plan_history (
        history_id UUID PRIMARY KEY,
        diet_plan_id UUID NOT NULL REFERENCES diet_plan(diet_plan_id),
        trainer_id VARCHAR NOT NULL,
        name VARCHAR NOT NULL,
        description TEXT NOT NULL,
        plan_type VARCHAR NOT NULL,
        target_calories INT NOT NULL,
        target_carbs FLOAT NOT NULL,
        target_protein FLOAT NOT NULL,
        target_fats FLOAT NOT NULL,
        actual_calories FLOAT NOT NULL,
        actual_carbs FLOAT NOT NULL,
        actual_protein FLOAT NOT NULL,
        actual_fats FLOAT NOT NULL,
        change_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP
    );
    ```
    - This table would store historical records of the diet plan whenever changes are made, along with a timestamp of the change.

```

```
