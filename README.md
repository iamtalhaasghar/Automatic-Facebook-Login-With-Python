# Automatic Facebook Login With Python [![forthebadge](https://forthebadge.com/images/badges/made-with-python.svg)](https://forthebadge.com)

---

## Overview

This is a Python script to automate the Facebook signup and login process. It uses Python 3.x and Selenium library with WebDriver to automate browser interactions.

### Features

- **Automated Facebook Sign Up**: Create new Facebook accounts with randomly generated user data
- **Automated Facebook Login**: Login to existing Facebook accounts
- **Headless Browser Support**: Run automation in headless mode for background execution
- **Fake Data Generation**: Automatically generate realistic user profiles using Faker library
- **Task Queue Support**: Scale signup operations using Celery task queue

---

## Prerequisites

- Python 3.x (3.7 or higher recommended)
- Firefox browser (GeckoDriver is used by default)
- Internet connection (for WebDriver installation and Facebook access)
- Redis server (optional, only needed for task queue functionality)

---

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/iamtalhaasghar/Automatic-Facebook-Login-With-Python.git
cd Automatic-Facebook-Login-With-Python
```

### 2. Install dependencies

Install all required packages using pip:

```bash
pip install -r requirements.txt
```

Or install packages individually:

```bash
pip install selenium
pip install webdriver-manager
pip install colored
pip install python-dotenv
pip install Faker
pip install random-password-generator
pip install psutil
pip install celery
pip install redis
pip install pandas
pip install numpy
```

### 3. Set up environment variables

Create a `.env` file in the project root directory:

```bash
touch .env
```

Add the following configuration to your `.env` file:

```env
# For sign-in functionality
EMAIL=your_email@example.com
PASS=your_password

# Facebook URL
FB_URL=https://www.facebook.com/

# Headless mode (True/False)
HEADLESS=False
```

### 4. Download GeckoDriver (if not auto-installed)

The script uses WebDriver Manager which automatically downloads the required driver. However, if you encounter issues, you can manually download GeckoDriver and place it in the project directory.

---

## Usage

### Run Facebook Sign Up (Main Script)

This will generate random user data and create a new Facebook account:

```bash
python facebook.py
```

### Run Facebook Sign In

To use the sign-in functionality, modify the `facebook.py` file and call:

```python
fb = Facebook()
fb.sign_in()
```

Make sure your credentials are properly set in the `.env` file.

### Run Bulk Sign Up with Task Queue

For creating multiple accounts in parallel:

1. Start Redis server:
```bash
redis-server
```

2. Start Celery worker:
```bash
celery -A tasks worker --loglevel=info
```

3. Run the test script:
```bash
python test.py
```

This will queue 100 signup tasks to be processed by Celery workers.

---

## Project Structure

- `facebook.py` - Main script containing Facebook class with sign_up and sign_in methods
- `fake.py` - Utility to generate fake user data using Faker library
- `tasks.py` - Celery task definitions for distributed signup operations
- `test.py` - Script to test bulk signup using Celery task queue
- `requirements.txt` - All Python dependencies
- `.env` - Environment variables (create this file yourself)

---

## Important Notes

### ⚠️ Legal and Ethical Considerations

- This tool is for **educational purposes only**
- Creating fake accounts or automating Facebook interactions may violate Facebook's Terms of Service
- Use this responsibly and at your own risk
- The authors are not responsible for any misuse of this tool

### Exception Handling

- If WebDriver is not installed, ensure you have a proper internet connection for automatic driver installation
- The script includes error handling and will display colored status messages
- Check the console output for detailed error messages if something goes wrong

### Browser Configuration

- The script currently uses Firefox with GeckoDriver
- Headless mode can be enabled by setting `HEADLESS=True` in the `.env` file
- Chrome support is commented out but can be enabled by modifying the code

---

## Troubleshooting

**Issue**: WebDriver not found
- **Solution**: Ensure you have internet connection for automatic driver download, or manually download GeckoDriver

**Issue**: Element not found errors
- **Solution**: Facebook's HTML structure may have changed. You might need to update the XPath/CSS selectors in the code

**Issue**: Script runs too fast
- **Solution**: Increase sleep timers in the code if needed for slower connections

**Issue**: Redis connection error
- **Solution**: Make sure Redis server is running before starting Celery workers

---

## Contributors

1. [Rohan Das](https://rohandas28.github.io/)
2. [Nikhil Raj Pandey](https://github.com/NikhilRajPandey)
3. [Sannidhya Dasgupta](https://github.com/Sannidhya127)

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## Acknowledgments

- Selenium WebDriver for browser automation
- Faker library for generating realistic test data
- Celery for distributed task queue functionality
