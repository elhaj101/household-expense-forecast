# Personal Household Expense Forecast

## Overview
This software helps users track their household expenses, analyze spending habits, and forecast savings. It provides a user-friendly interface and integrates with Google Sheets for data storage. it is not focused on tracking spending rather focused on setting spendings and savings thresholds and goals all while helping the user prioritise spending in the household on different criterias.

## Functionality
The software includes key functions such as:

- Greeting the user based on the time of day.
- Displaying a list of predefined spending categories.
- Collecting the user's name and monthly salary, with input validation.
- Collecting monthly spending amounts for each category.
- Showing a menu with various options for user interaction.
- Calculating current monthly and annual savings based on salary and spending.
- Allowing users to analyze potential savings by reducing spending in selected categories.
- Forecasting savings and expenses over the next 12 months.
- Saving user data to a Google Sheet.
- Loading user data from a Google Sheet.
- Resetting the system to clear user data.
- Quitting the system with a farewell message.
- Running the main program and managing user interactions.

## Readability
The code is structured to be readable, following proper indentation and including comments that clarify the purpose of functions and sections.

## Input Data Handling
The code includes multiple input validations to ensure that user data is correct. Here are the key aspects:

1. Name Input Validation
   - The name must only contain letters and spaces. If invalid, the user is prompted to re-enter it.

2. Salary Input Validation
   - Salary must be a positive number. Negative or non-numeric inputs prompt the user to re-enter.

3. Spending Amount Validation
   - Spending amounts for each category must be non-negative numbers. Invalid inputs prompt re-entry.

4. Menu Option Validation
   - Users must select valid menu options. Invalid selections prompt re-entry.

5. Category Selection Validation
   - Users must enter valid category numbers. Invalid inputs prompt re-entry.

6. Percentage Reduction Validation
   - The percentage reduction for a category must be between 0 and 100. Invalid inputs prompt re-entry.

7. Google Sheets Data Validation
   - The number of data columns must match the headers in the Google Sheet. Mismatches prevent saving.

8. Data Loading Validation
   - The program checks if the user's name exists in the Google Sheet. If not found, an error message appears.

9. Error Handling
   - Errors during Google Sheets API operations are caught and managed gracefully, providing user feedback.

### Summary of Input Handling
- Data type validation ensures inputs are correct.
- Range validation confirms inputs are within acceptable limits.
- Format validation checks that inputs meet expected patterns.
- Error handling provides clear prompts for invalid inputs.
- Data integrity ensures saved and loaded data is consistent.

## Code Structure
The code is organized into small functions, each addressing specific tasks. This modular approach enhances readability, maintainability, and testing.

## Testing
The software has undergone manual testing and debugging to verify functionality. Linter checks were conducted to maintain code quality.

## Conclusion
Future enhancements will include:

- Implementing visualizations and graphs for the forecast function to offer better insights into spending and savings.
- Using the geolocation API to greet users based on their location, adding a personalized touch to the experience.