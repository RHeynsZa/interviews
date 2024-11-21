# Advanced Weather Data Analysis

## Introduction

This challenge is inspired by the ["1 Billion Row Challenge"](https://1brc.dev/) but for simplicity, you will be working with a subset of just 100000 rows of data. The goal is to write an efficient function to calculate the minimum, maximum, and mean temperature for each city in the dataset.

Each row in the dataset contains a city name and its temperature (in Celsius), separated by a semicolon. For example:
```
Hamburg;12.0  
Bulawayo;8.9  
Palembang;38.8  
Hamburg;34.2  
St. John's;15.2  
Cracow;12.6  
```


The goal is to analyze and process the data efficiently, handle errors robustly, and think critically about scaling the solution to much larger datasets. There are 2 files in this repository:
- `measurements-10.txt` contains 10 rows of data
- `measurements-100000.txt` contains 100000 rows of data

The questions will have a slightly altered version of the dataset, so you can test your solution with the 10-row file before running it on the 100000-row file. These files are tagged per question in the following format:
- `measurements-10-q1.txt` for question 1
- `measurements-10-q2.txt` for question 2
and the same for the 100000-row file.

You can use the 10-row file to test your solution, but the final solution should be able to handle the 100000-row file.

The language you choose is up to you, but you should be able to explain your code and thought process. Try to write a production-quality solution that you would be proud to ship to customers, and that you would be happy for other developers to review. 

**NOTE**
This test should be possible to finish in an hour, and you should not have to spend more than two hours on this. You do not have to implement repetitive actions like testing every possible case. You may demonstrate a few cases and write comments outlining what else would be required. 

If you find that all the things you want to do are going to greatly exceed the time, write more comments describing your preferred improvements.

You may ask questions when you wish, you may google and use whatever tools you like. Asking questions does not count against you. The purpose of this test is to provide you with a task to demonstrate your ability to write quality code and show you understand the task.

### Evaluation Criteria

Note that the test is broken down into 3 parts:
- Part 1: Practical coding questions
- Part 2: System design question
- Part 3: Theoretical questions

## Part 1: Practical Coding Questions

### 1. Optimized Aggregation

We want to calculate the minimum, maximum, and mean temperature for each city in the dataset. The dataset may contain multiple entries for the same city.

### Instructions

Write an efficient function to calculate the following statistics for each city:
- Minimum temperature
- Maximum temperature
- Mean temperature (rounded to 1 decimal place)

You're going to need to write a function that reads the data from a file, processes it, and returns the statistics for each city. The function should be able to handle the 100000-row file.

```
{
    "Hamburg": {"min": 12.0, "max": 34.2, "mean": 23.1},
    "Bulawayo": {"min": 8.9, "max": 8.9, "mean": 8.9},
    "Palembang": {"min": 38.8, "max": 38.8, "mean": 38.8},
    "St. John's": {"min": 15.2, "max": 15.2, "mean": 15.2},
    "Cracow": {"min": 12.6, "max": 12.6, "mean": 12.6}
}
```

### 2. Error Handling
The dataset may contain corrupted or incomplete rows, such as:

```
Hamburg;12.0
Bulawayo;abc
Palembang;38.8
Hamburg;
```
### Instructions

Update your function to:

- Skip rows with missing or invalid temperature values.
- Log each invalid row along with a brief error description (e.g., "Bulawayo;abc" - Invalid temperature format).
- If a city has only invalid data, ensure it does not appear in the final output.

## Part 2: System Design Question

### 1. City Name Normalization
Data in the dataset can come from various sources, each using inconsistent formats for city names and abbreviations. To address this inconsistency, you need to design a system that normalizes city names and handles ambiguous input.

For example, here is a mapping of canonical city names to possible variations or abbreviations:
```
"Hamburg" → ["HAMBURG", "hamburg", "Ham burg"]
"St. John's" → ["St johns", "st john's", "st. john's"]
"Cracow" → ["Crakow", "cracow", "Krakow"]
"Goteborg" → ["Göteborg", "goteborg", "Gothenburg"]
"New York" → ["NY", "New York", "new york", "the big apple"]
"Dallas" → ["Dallas", "dallas", "DFW"]
```

### Instructions

*NOTE:* This question does not require you to write code. Instead, you should describe how you would design a system to normalize city names and handle ambiguous input. You can write pseudocode or describe the steps you would take to implement this system. Think about how you would handle edge cases and ensure the system is scalable and efficient.

## Part 3: Theoretical Questions

In a real-world scenario, this data would likely be part of a larger system. The data might come from a database, an API, or a message queue, or even a mix of these sources. The system would need to be scalable, secure, and maintainable.

### 1. Scalability
The dataset was taken from the 1 Billion Row Challenge, which contains 1 billion rows of data. How would you modify your solution to handle this scale? Consider your scaling approach.
### 2. Security
Since the data could possibly come externally, how would you ensure the security of the system? What security considerations would you take into account?
### 3. Maintainability
How would you ensure that your system is maintainable by other developers? What would you do to make your code more readable and maintainable? How would you ensure that your system is easy to debug and test?
