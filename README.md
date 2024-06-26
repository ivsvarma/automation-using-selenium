# Campus Job Portal Automation with Selenium and AI

## Description

This project automates interactions with a campus job portal using Selenium WebDriver. The goal is to streamline the job search and application process for students by automating repetitive tasks.

## Features

- **Automated Login**: Log in to the campus job portal automatically using stored credentials.
- **Job Search Automation**: Search for jobs based on predefined criteria such as job title, location, and company.
- **Application Submission**: Automatically fill out and submit job applications.
- **Profile Management**: Keep the user's profile updated with the latest information.
- **Job Alerts**: Receive alerts for new job postings that match user preferences.
- **AI Resume Screening**: Utilize machine learning to screen and match resumes with job descriptions.
- **Data Extraction**: Extract job details for further analysis and processing.
- **Notification System**: Get notifications about application statuses and new job postings.

## Technologies Used

- **Python**: Main programming language for scripting and automation.
- **Selenium WebDriver**: For automating web browser interactions.
- **BeautifulSoup**: For web scraping and data extraction.
- **Scikit-learn**: For machine learning algorithms.
- **Pandas**: For data manipulation and analysis.
- **Email API**: To send notifications.

## Installation

1. **Clone the Repository**:
    ```sh
    git clone https://github.com/your-username/campus-job-portal-automation.git
    cd campus-job-portal-automation
    ```

2. **Create and Activate a Virtual Environment**:
    ```sh
    python -m venv venv
    source venv/bin/activate   # On Windows, use `venv\Scripts\activate`
    ```

3. **Install Dependencies**:
    ```sh
    pip install -r requirements.txt
    ```

4. **Run the Automation Script**:
    ```sh
    python automation_script.py
    ```

## Usage

1. **Update the Script with Your Credentials**:
    - Open `automation_script.py` and enter your email and password in the appropriate fields:
      ```python
      username.send_keys("your_email@example.com")
      password.send_keys("your_password")
      ```

2. **Run the Script**:
    - Execute the script to start the automation process:
      ```sh
      python automation_script.py
      ```

## Code Example

Here is a snippet of the automation script:

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.chrome.options import Options
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
import time

options = Options()
options.add_experimental_option("detach", True)
driver = webdriver.Chrome(options=options)
driver.get("https://srmktr.pod.ai/login")
driver.maximize_window()

wait = WebDriverWait(driver, 20)

# Log in to the portal
username = wait.until(EC.element_to_be_clickable((By.XPATH, "//input[@name='email' and @type='text']")))
username.send_keys("your_email@example.com")
time.sleep(1)
print("Email entered successfully")

password = wait.until(EC.element_to_be_clickable((By.XPATH, "//input[@data-ng-model='ngModel' and @placeholder='Password*']")))
password.send_keys("your_password")
time.sleep(1)
print("Password entered successfully")

login_button = wait.until(EC.element_to_be_clickable((By.XPATH, "//span[text()='Log in']")))
login_button.click()
time.sleep(1)
print("Log in button clicked")

opportunities_link = wait.until(EC.element_to_be_clickable((By.XPATH, "(//a[@href='/d/5iIkJe/opportunities/'])[1]")))
opportunities_link.click()
time.sleep(1)
print("Clicked on Opportunities link")

first_gutter_div = wait.until(EC.element_to_be_clickable((By.CSS_SELECTOR, ".infinite-scroll-component.infinite-scroller-wrap .gutter-width-y:first-child")))
first_gutter_div.click()
time.sleep(1)
print("Clicked on the first gutter-width-y div")

apply_click = wait.until(EC.element_to_be_clickable((By.XPATH,"//button[@class='MuiButtonBase-root MuiButton-root MuiButton-contained MuiButton-containedPrimary MuiButton-sizeSmall MuiButton-containedSizeSmall MuiButton-disableElevation MuiButton-fullWidth MuiButton-root MuiButton-contained MuiButton-containedPrimary MuiButton-sizeSmall MuiButton-containedSizeSmall MuiButton-disableElevation MuiButton-fullWidth css-1ukc7ik-ButtonV5-root-ButtonV5-contained-ButtonV5-root-ButtonV5-contained']")))
apply_click.click()
time.sleep(2)

checkbox1 = wait.until(EC.presence_of_element_located((By.XPATH, "//label[contains(@class, 'MuiFormControlLabel-root') and contains(@class, 'MuiFormControlLabel-labelPlacementEnd') and contains(@class, 'css-1rvga7b-Checkbox-formControlLabelRoot')]")))
checkbox1.click()
time.sleep(1)

yes_ready = wait.until(EC.element_to_be_clickable((By.XPATH, "//button[contains(@class, 'MuiButtonBase-root') and contains(@class, 'MuiButton-root') and contains(@class, 'MuiButton-contained') and contains(@class, 'MuiButton-containedPrimary') and contains(@class, 'MuiButton-sizeSmall') and contains(@class, 'MuiButton-containedSizeSmall') and contains(@class, 'MuiButton-disableElevation') and contains(@class, 'css-ppxypf-ButtonV5-root-ButtonV5-contained') and contains(., 'Yes I am Ready')]")))
yes_ready.click()
print("Clicked on 'Yes I am Ready' button")
time.sleep(1)

checkboxes2 = wait.until(EC.presence_of_all_elements_located((By.XPATH, "//input[@type='checkbox' and @class='PrivateSwitchBase-input css-1m9pwf3']")))
for checkbox in checkboxes2:
    checkbox.click()
    print("Clicked on checkbox")
time.sleep(1)

next_button = wait.until(EC.element_to_be_clickable((By.XPATH, "//button[contains(@class, 'MuiButtonBase-root') and contains(@class, 'MuiButton-root') and contains(@class, 'MuiButton-contained') and contains(@class, 'MuiButton-containedPrimary') and contains(@class, 'MuiButton-sizeSmall') and contains(@class, 'MuiButton-containedSizeSmall') and contains(@class, 'MuiButton-disableElevation') and contains(@class, 'css-ppxypf-ButtonV5-root-ButtonV5-contained') and contains(., 'Next')]")))
next_button.click()
print("Clicked on the 'Next' button")
time.sleep(1)

programming_level = wait.until(EC.element_to_be_clickable((By.XPATH,"//div[contains(@class, 'MuiSelect-root') and contains(@class, 'MuiSelect-select') and contains(@class, 'MuiSelect-selectMenu') and contains(@class, 'MuiSelect-outlined') and contains(@class, 'MuiInputBase-input') and contains(@class, 'MuiOutlinedInput-input') and p[text()='Select']]")))
programming_level.click()
level = wait.until(EC.element_to_be_clickable((By.XPATH,"//li[contains(@class, 'MuiButtonBase-root')      and contains(@class, 'MuiListItem-root')      and contains(@class, 'MuiMenuItem-root')      and contains(@class, 'multiple')      and contains(@class, 'MuiMenuItem-gutters')      and contains(@class, 'MuiListItem-gutters')      and contains(@class, 'MuiListItem-button')      and .//span[@class='MuiFormLabel-root MuiFormLabel-colorPrimary css-123611g-FormLabel-root' and text()='Intermediate']]")))
level.click()
time.sleep(1)

elements = driver.find_elements(By.XPATH, "//div[contains(@class, 'MuiFormControl-root') and contains(@class, 'MuiTextField-root') and contains(@class, 'MuiFormControl-fullWidth')]//input[@placeholder='Sample Text']")
values_to_send = ["Your Skills", "Your LeetCode Account", "Your GitHub Link", "Your Projects"]
for i in range(len(elements)):
    element = elements[i]
    value = values_to_send[i]
    
    # Ensure element is visible and enabled before sending keys
    WebDriverWait(driver, 10).until(EC.visibility_of(element))
    element.send_keys(value)
time.sleep(1)

next_button = wait.until(EC.element_to_be_clickable((By.XPATH, "//button[contains(@class, 'MuiButtonBase-root') and contains(@class, 'MuiButton-root') and contains(@class, 'MuiButton-contained') and contains(@class, 'MuiButton-containedPrimary') and contains(@class, 'MuiButton-sizeSmall') and contains(@class, 'MuiButton-containedSizeSmall') and contains(@class, 'MuiButton-disableElevation') and contains(@class, 'css-ppxypf-ButtonV5-root-ButtonV5-contained') and contains(., 'Next')]")))
next_button.click()
print("Clicked on the 'Next' button")
