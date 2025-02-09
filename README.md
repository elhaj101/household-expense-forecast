# Personal Household Expense Forecast

## Overview
This software helps users track their household expenses, analyze spending habits, and forecast savings. It provides a user-friendly interface and integrates with Google Sheets for data storage. it is not focused on tracking spending rather focused on setting spendings and savings thresholds and goals all while helping the user prioritise spending in the household on different criterias.

Here's the entire section formatted in Markdown:

```markdown
## Running the Software

You can run this CLI software by either forking/cloning the repository or using the Heroku deployed sandbox environment.

### Option 1: Forking/Cloning the Repository

1. **Fork the Repository**: Click the "Fork" button on the top right of this repository to create your own copy.

2. **Clone the Repository**: Open your terminal and run the following command to clone your forked repository:

   ```bash
   git clone https://github.com/your-username/repository-name.git
   ```

   Replace `your-username` and `repository-name` with your GitHub username and the name of this repository.

3. **Navigate to the Directory**:

   ```bash
   cd repository-name
   ```

4. **Install Dependencies**: Make sure you have Python 3 installed. Then, install the required packages by running:

   ```bash
   pip install -r requirements.txt
   ```

5. **Run the Software**: You can now run the software using:

   ```bash
   python3 your_script.py
   ```

   Replace `your_script.py` with the name of the main Python file.

   ![Placeholder Image](assets/images/python3.png)


### Option 2: Using the Heroku Deployed Sandbox Environment

1. **Access the Deployed Application**: Navigate to the URL of your Heroku deployed application. You can find this in your Heroku dashboard.

2. **Interact with the CLI**: Follow the instructions provided in the application interface to interact with the CLI features.

### Additional Notes

- Ensure you have the necessary environment variables set up in Heroku if your application requires them.
- For any issues, please refer to the troubleshooting section or open an issue in this repository.



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

 ![Placeholder Image](assets/images/validation.png)

 score: 8.89



 # Steps to Enable Google Sheets API

## Step 1: Create a Google Cloud Project
1. Go to the **Google Cloud Console**.
2. Click on the project drop-down and select **New Project**.
3. Enter a name for your project and click **Create**.

## Step 2: Enable the Google Sheets API
1. In  project dashboard, click on **APIs & Services** > **Library**.
2. Search for "Google Sheets API" and click on it.
3. Click **Enable**.

## Step 3: Create Service Account
1. Navigate to **APIs & Services** > **Credentials**.
2. Click on **Create Credentials** and select **Service Account**.
3. Fill in the service account details (name, description) and click **Create**.
4. In the next step, you can assign roles. For basic access, select **Editor** or **Viewer**. Click **Continue**.
5. Click **Done**.

## Step 4: Generate Service Account Key
1. After creating the service account, you will be redirected to the service accounts page. Click on the service account you just created.
2. Go to the **Keys** tab and click **Add Key** > **Create New Key**.
3. Choose **JSON** as the key type and click **Create**. This will download a JSON file containing your service account credentials (e.g., `creds.json`).

## Step 5: Share Google Sheet with Service Account
1. Open the Google Sheet you want to access.
2. Click on the **Share** button in the top right corner.
3. In the **Share with people and groups** window, enter the client email from your downloaded JSON file (it looks like `your-service-account@your-project.iam.gserviceaccount.com`).
4. Set the permissions (e.g., **Viewer** or **Editor**) and click **Send**.

## Step 6: Link to Your Code
1. Ensure your `creds.json` file (the one you downloaded) is in the same directory as your Python script.
2. In your Python script, add the following lines to authenticate and access your Google Sheet:

    ```python
    from google.oauth2.service_account import Credentials
    import gspread

    SCOPE = [
        "https://www.googleapis.com/auth/spreadsheets",
        "https://www.googleapis.com/auth/drive.file",
        "https://www.googleapis.com/auth/drive"
    ]

    CREDS = Credentials.from_service_account_file('creds.json')
    SCOPED_CREDS = CREDS.with_scopes(SCOPE)
    GSPREAD_CLIENT = gspread.authorize(SCOPED_CREDS)
    SHEET = GSPREAD_CLIENT.open("expense_tracker")  # Replace with your Google Sheet name
    ```

## Step 7: Run Your Code
Now that everything is set up, you can run your Python script. It should authenticate with the Google Sheets API and interact with your specified Google Sheet without any issues.


### Issue and solution

- issue:
 Repeated saves create duplicate entries instead of updating.
 ![Placeholder Image](assets/images/issue1.png)
 ![Placeholder Image](assets/images/issue1.2.png)

- solution:  

- Get the worksheet.
- Get all records as a list of dictionaries.
- Loop through each record, check if the 'Name' matches.
- If found, note the index, calculate the row number (index + 2).
- Prepare the row data as a list, same as before.
- Use sheet.update(row_number, [row_data]) to update that row.
- If not found, append the row as before.
![Placeholder Image](assets/images/solution1.png)


## Deployment Steps

This section outlines the steps taken to deploy the software on Heroku and connect it with GitHub.

### Prerequisites

- Ensure you have a Heroku account.
- Install the Heroku CLI on your local machine.
- Have your GitHub repository ready.

### Steps to Deploy

1. **Log in to Heroku**:
   Open your terminal and log in to your Heroku account:

   ```bash
   heroku login

- Create a New Heroku Application:
```bash
heroku create your-app-name
```

- Link Your GitHub Repository:
```bash
heroku git:remote -a your-app-name
```
- Set Up Environment Variables:
```bash
heroku config:set VARIABLE_NAME=value
```
- Deploy the Application:
```bash
git push heroku main
```

- Open Your Application:
```bash
heroku open
```

- Monitor Logs:
To check the logs for any issues, use:
```bash
heroku logs --tail
```
## Conclusion

Future enhancements will include:

- Implementing visualizations and graphs for the forecast function to offer better insights into spending and savings.
- Using the geolocation API to greet users based on their location, adding a personalized touch to the experience.