# Automatic Facebook Login With Python [![forthebadge](https://forthebadge.com/images/badges/made-with-python.svg)](https://forthebadge.com)

---

## Overview

This is a Python script to automate both **login** and **signup** processes on Facebook.com. It uses Python 3.x and Selenium library to automate browser interactions, with support for headless mode, fake data generation, and distributed task processing.

---

## Features

- **Automated Facebook Login**: Automatically log into Facebook using stored credentials
- **Automated Facebook Signup**: Create new Facebook accounts with randomly generated user data
- **Fake Data Generation**: Generate realistic user profiles using the Faker library
- **Headless Browser Mode**: Run browser automation in the background without GUI
- **Resource Monitoring**: Track CPU and memory usage during automation
- **Celery Task Queue**: Distribute signup tasks across multiple workers for parallel processing
- **Environment Configuration**: Use `.env` file for secure credential management

---

## Installation

### 1. Install Dependencies

Install all required packages using pip:

```bash
pip install -r requirements.txt
```

Or install individually:

```bash
pip install selenium webdriver-manager colored python-dotenv faker celery redis psutil random-password-generator pandas numpy
```

### 2. WebDriver Setup

The script uses Firefox WebDriver (geckodriver). Ensure you have:
- Firefox browser installed
- `geckodriver` executable in the project directory or system PATH

**Note**: If drivers are not installed, you need proper internet connection to automatically download required drivers.

### 3. Environment Configuration

Create a `.env` file in the project root with the following variables:

```env
# Facebook credentials for login
EMAIL=your-email@example.com
PASS=your-password

# Facebook URL
FB_URL=https://www.facebook.com/

# Headless mode (True/False)
HEADLESS=False
```

### 4. Redis Server (for Celery)

If using the task queue functionality, ensure Redis is running:

```bash
redis-server
```

---

## Usage

### Sign In (Login)

To login to an existing Facebook account:

```python
from facebook import Facebook

fb = Facebook()
fb.sign_in()
```

Or run the facebook.py directly and modify the `__main__` section.

### Sign Up (Create Account)

To create a new Facebook account with fake data:

```python
from facebook import Facebook
from fake import get_data

user_data = get_data()
fb = Facebook()
fb.sign_up(user_data)
```

Or run directly:

```bash
python facebook.py
```

### Distributed Task Processing

Start Celery worker:

```bash
celery -A tasks worker --loglevel=info
```

Run multiple signups:

```bash
python test.py
```

This will queue 100 signup tasks that will be processed by Celery workers.

---

## File Structure

- **facebook.py**: Main automation script with Facebook class
- **fake.py**: Fake data generator for creating random user profiles
- **tasks.py**: Celery task definitions for distributed processing
- **test.py**: Test script for bulk signup operations
- **requirements.txt**: All Python dependencies

---

## Requirements

Key dependencies:
- selenium >= 4.9.0
- webdriver-manager >= 3.8.6
- colored >= 1.4.4
- python-dotenv >= 1.0.0
- Faker >= 18.6.0
- celery >= 5.2.7
- redis >= 4.5.4
- psutil >= 5.9.5
- pandas >= 2.0.1
- numpy >= 1.24.3
- random-password-generator >= 2.2.0

---

## Using this with Proxy

For a professional approach to using proxies in your automation processes, I recommend NodeMaven's Residential Proxies. Having tried numerous proxy providers, I find NodeMaven excels in simplicity and usefulness.

Here's how to get started:

1. Register on the NodeMaven platform using this [link](https://go.nodemaven.com/rohandas).
2. Select the trial option on your personal account.
3. Use 500FREE at checkout to receive +2GB of free proxy when purchasing any package (except trial). Try NodeMaven now - [NodeMaven Proxies](https://go.nodemaven.com/rohandas).

---

## Notes

- **Ethical Use**: This tool is for educational purposes only. Automated account creation may violate Facebook's Terms of Service.
- **Rate Limiting**: Facebook may block or throttle automated requests. Use responsibly.
- **Headless Mode**: Enable headless mode in `.env` for background execution without GUI.

---

## Contributors

1. [Rohan Das](https://rohandas28.github.io/)
2. [Nikhil Raj Pandey](https://github.com/NikhilRajPandey)
3. [Sannidhya Dasgupta](https://github.com/Sannidhya127)
4. [Talha Asghar](https://github.com/iamtalhaasghar)

---
