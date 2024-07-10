## Shapefitio: Gym Trainer Management Application

Shapefitio is an application that helps gym trainers manage their clients by assigning diet plans, workouts, and programs. The app specifies the exercises clients need to do, the time they will take, the rest time between each set and many more

### Key Features

- Trainers can create diet plans and assign them to many clients. The duration of the diet plan can be 1 week, 2 weeks, 4 weeks or months.

- Trainers can create programs and assign them to many clients. The duration of the program can be 1 week, 2 weeks, or 4 weeks.

- Trainers can create a 2000-calorie diet plan and assign it to multiple clients based on their requirements. This helps trainers reduce time spent and manage more clients efficiently.

- Trainers can create a specific program and assign it to multiple clients based on their requirements. This helps trainers reduce time spent and manage more clients efficiently.

- Reduces the workload of trainers by allowing them to reuse diet plans and programs.

- Helps trainers manage a larger number of clients in less time.

### Team Development

- Our team of six has developed and is constantly enhancing Shapefitio for advanced customer engagement.

## Table of Contents

- [My Learnings](#my-learnings-from-the-internship)
- [Food Items](#food-items)
- [DietPlan](#dietPlan)
- [Assign DietPlan to Client](#assign-dietPlan-to-client)
- [Habits](#habits)
- [Exercise Feature](#exercise-feature)
- [Workouts](#workouts)
- [Programs](#programs)

## My Learnings from the Internship

### Key Learnings

1. **State Management in React with MobX**

   - Learned to manage states and data effectively using MobX stores.

2. **Frontend Integration with API Calls**

   - Gained experience in integrating the frontend with API calls and handling errors by displaying them on the frontend.

3. **Ant Design (Antd)**

   - Used Ant Design, the world's second most popular React UI framework, to design complex UIs.

4. **UI Functionalities Implementation**

   - Implemented functionalities such as creating, editing, searching, and deleting items, diet plans, workouts, programs, habits, and client diet plans.

5. **Code Structure and Reusability**

   - Learned to write structured code and create reusable components for future usage.

6. **Git and Version Control**

   - Enhanced knowledge of Git, including creating pull requests, resolving PR comments, and understanding the need for branches (testing and master/main branch for deployment).

7. **Spring Boot**

   - Built APIs, especially for habits, using Spring Boot.

8. **Drag and Drop Functionality**

   - Implemented drag and drop functionality in the application.

9. **Dynamic Label Updates**
   - Learned to dynamically update label information when data changes in the input fields.

**During the internship, I worked on and implemented end-to-end features. Let us go over them one by one with videos to help you understand my work better.**

## Food Items

https://github.com/cnu1328/InterviewPrep/assets/110097436/c53d3a0c-4554-4d61-b577-1b7ccb0bbd6f

### Features

1. **Create Food Items**

   - A trainer can create a food item with values for calories, proteins, carbohydrates, and fats available in the portion`(quantity)` measurement`(like grams)` of the food item. For example, a trainer can create a food item like rice.

2. **Save Multiple Food Items**

   - A trainer can save multiple food items in the database.

3. **Search Food Items**

   - Implemented functionality to easily search for food items.

4. **Modify Food Items**

   - A trainer can modify existing food items.

5. **View Food Items**

   - A trainer can view the details of a food item.

6. **Delete Food Items**
   - A trainer can delete a food item from the system.

### Example Food Items

| Food Item | Calories (per 100g) | Proteins (per 100g) | Carbohydrates (per 100g) | Fats (per 100g) |
| --------- | ------------------- | ------------------- | ------------------------ | --------------- |
| Rice      | 130                 | 2.4                 | 28                       | 0.3             |
| Chicken   | 165                 | 31                  | 0                        | 3.6             |

## DietPlan

### Overview

This feature helps trainers create a diet plan with the required amounts of calories, proteins, fats, and carbohydrates. To create a DietPlan, it uses the food items created beforehand.

### Create a DietPlan

1. **Provide DietPlan Details**

   - The trainer needs to give the diet plan a name and specify the target amounts for calories, proteins, fats, and carbohydrates.

2. **Create Meals for the DietPlan**

   - The trainer creates different meals for the diet plan, such as Breakfast, Lunch, Pre Workout, Post Workout, Snacks, and Dinner.

3. **Select Food Items for Each Meal**
   - For each meal, the trainer selects food items. Below are examples of food items:

| Food Item | Calories (per 100g) | Proteins (per 100g) | Carbohydrates (per 100g) | Fats (per 100g) |
| --------- | ------------------- | ------------------- | ------------------------ | --------------- |
| Rice      | 130                 | 2.4                 | 28                       | 0.3             |
| Chicken   | 165                 | 31                  | 0                        | 3.6             |

4. **Search and Select Food Items**

   - Trainers can search for food items and select the required ones. When a food item is selected, all fields (calories, proteins, fats, and carbohydrates) are automatically filled according to the values of the food item.

5. **Adjust Portion Sizes**

   - Trainers can change the portion (quantity) of the food item, which will affect the amount of calories, proteins, carbohydrates, and fats.

6. **View Total Nutrients**

   - Trainers can see the total amounts of calories, proteins, carbohydrates, and fats for each meal.
   - The UI also displays the total amounts for all meals combined.
   - It shows the remaining amounts of calories, proteins, carbohydrates, and fats needed to reach the target or if the target has been exceeded.

7. **Validation**
   - Added validations ensure that the user must pass all checks to create a diet plan.

## Assign DietPlan to Client

### Overview

**Client DietPlans**:

- Trainers can assign, modify, and delete diet plans for clients.

### Assign DietPlan UI

**Viewing DietPlans**:

- The UI shows all the diet plans that have been created.

**Assigning a DietPlan**:

- Trainers can select one diet plan to assign.
- Trainers can set the start date and end date for the diet plan, indicating when the client should follow it.

**Creating a New DietPlan**:

- If the trainer wants to create a new diet plan with overlapping dates, the system handles this by:
  - Informing the trainer about the overlap.
  - Giving the trainer the option to override the previously assigned diet plan or cancel the new assignment.

### Use of Client DietPlans Feature

The Client DietPlans feature helps trainers manage their clients' diet plans effectively. Here’s how it helps:

1. **Organization**: Trainers can easily assign, modify, and delete diet plans for their clients, keeping their plans organized.
2. **Flexibility**: The ability to select start and end dates for diet plans allows trainers to customize the duration for each client.
3. **Conflict Management**: The system handles overlapping diet plans by informing trainers and providing options to resolve the conflict, ensuring clients follow the correct plan.
4. **Efficiency**: Viewing all created diet plans in one place and selecting the desired plan quickly saves trainers time.

This feature improves the Shapefitio platform by enabling trainers to efficiently manage detailed diet plans for their clients, leading to better adherence to diet plans and improved client results.

## Habits

### Overview

Trainers can create and manage habits to help clients improve their routines and overall well-being. Examples of habits include meditation, walking, and reading.

### Features

1. **Create Habits**

   - Trainers can create new habits, such as meditation, walking, reading, and more.

2. **Search Habits**

   - Implemented functionality to easily search for existing habits.

3. **Modify Habits**

   - Trainers can modify the details of existing habits.

4. **Delete Habits**
   - Trainers can delete habits that are no longer needed.

### Benefits

- **Assign Habits to Clients**
  - Trainers can assign these habits to their clients, helping them to adopt and maintain healthy routines.

By using these features, trainers can efficiently manage and assign habits to their clients, contributing to their overall development and well-being.

## Exercise Feature

The exercise feature allows trainers to add new exercises to the app's database with comprehensive details. This feature is crucial for the following reasons:

1. **Personalization**: Trainers can customize workout programs to suit individual client needs by creating specific exercises targeting different focus areas and categories.

2. **Efficiency**: By tagging exercises with relevant keywords, trainers and clients can easily search and filter exercises, saving time and enhancing the user experience.

3. **Clarity**: Providing detailed descriptions and media links ensures that clients understand how to perform each exercise correctly, reducing the risk of injury and improving workout effectiveness.

4. **Consistency**: Standardizing exercise details helps maintain consistency across different trainers and programs within the app, ensuring a cohesive training experience for all clients.

This feature enriches the Shapefitio platform by enabling trainers to offer more varied and tailored workout programs, ultimately enhancing client satisfaction and fitness outcomes.

## Workouts

### Overview

**Workouts**:

- A trainer can create a workout, search workouts, modify workouts, and delete workouts.

### Workout Creation

**Create Workout UI**:

- Trainers can see previously created exercises.
- Trainers can search, drag, and drop exercises to create workouts.

### Implemented Functionalities

1. **Dragging Multiple Exercises**: Trainers can drag multiple exercises into the workout.

2. **Deleting Dragged Exercises**: Trainers can remove exercises that have been added to the workout.

3. **Deleting Sets**: Trainers can delete sets from exercises.

4. **Creating Multiple Sets**: Trainers can create multiple sets at a time for each exercise.

**Use of Workout Feature**:

The workout feature lets trainers create, modify, search for, and delete workouts in the Shapefitio app. This feature is important for several reasons:

1. **Personalization**: Trainers can customize workouts to fit each client's needs by mixing different exercises and adjusting sets, weights, repetitions, and rest times.

2. **Efficiency**: The drag-and-drop and search features make creating workouts quicker and easier.

3. **Flexibility**: Trainers can easily update workouts by adding or removing exercises and sets, keeping workouts fresh and adaptable.

4. **Clarity**: Detailed workout plans help clients understand their training schedule, leading to better commitment and results.

5. **Consistency**: Standardized workout creation and management ensure a uniform training experience across different trainers and programs in the app.

This feature improves the Shapefitio app by allowing trainers to quickly and effectively create and manage workouts, leading to happier clients and better fitness outcomes.

## Programs

### Overview

**Programs**:

- Trainers can create, search for, delete, and modify programs.

### Program Creation

**Program Duration**:

- Trainers can create programs with durations of 1 week, 2 weeks, or 4 weeks.

**Create Program UI**:

- If the trainer selects four weeks, they see a 4-week view by default.
- Trainers can also view the program in 2-week and 1-week views.

**Daily Options**:

- For each day, trainers can:
  - Set the day as a rest day.
  - Assign workouts to the day.

### Workout Assignment

**Adding Workouts**:

- Trainers can see previously added workouts.
- Trainers can search for workouts for quicker access.
- Trainers can select multiple workouts for a day.
- Trainers can modify the workouts for that day.

**Deleting Workouts**:

- Trainers can delete added workouts from a day.

### Week Management

**Copy and Paste Workouts**:

- Trainers can copy workouts assigned for an entire week.
- Trainers can paste these workouts into other weeks, making it easier to assign workouts for all days.

**Deleting Weeks**:

- Trainers can delete the entire week at once.

### Use of Program Feature

The program feature helps trainers by allowing them to easily manage and organize workout plans over several weeks. Here's how it helps:

1. **Customization**: Trainers can create programs that fit their clients' needs by choosing the duration and assigning specific workouts.

2. **Efficiency**: The ability to search, add, and modify workouts quickly helps trainers save time.

3. **Flexibility**: Trainers can adjust the program by changing workouts for specific days, ensuring the program stays relevant and effective.

4. **Convenience**: The copy and paste feature allows trainers to quickly replicate workouts across different weeks, streamlining the program creation process.

5. **Simplicity**: The option to view programs in different durations (1 week, 2 weeks, 4 weeks) and delete entire weeks makes program management straightforward.

This feature enhances the Shapefitio platform by enabling trainers to efficiently create and manage detailed workout programs, leading to improved client satisfaction and fitness results.
