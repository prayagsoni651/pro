# Flipkart Scraper Project 🕷️🛒

## Project Description
The **Flipkart Scraper** is a Python-based web application designed to extract product reviews, ratings, and pricing information from Flipkart. Built using **Flask**, **Selenium**, and **MongoDB**, it allows users to search for products and analyze customer feedback in real-time. The application provides a user-friendly interface to view scraped data and visualizes sentiment trends through graphs.

## Problem Solved 💡
In the e-commerce world, making informed purchasing decisions can be difficult due to the sheer volume of products and reviews.
- **For Buyers**: It saves time by aggregating reviews and ratings into a single view, allowing for quick comparison.
- **For Sellers/Analysts**: It provides a way to gather competitive intelligence and sentiment analysis on products without manual data entry.

## Features 🚀
- **Real-time Scrapping**: Fetches live data from Flipkart using Selenium.
- **Review Analysis**: Extracts customer names, ratings, comments, and review age.
- **Data Persistence**: Stores scraped data in a MongoDB database to avoid redundant scraping.
- **Visualizations**: Generates scatter plots to visualize the relationship between products and their ratings.
- **CSV Export**: Automatically saves scraped data to a CSV file for offline analysis.
- **Web Interface**: Simple and intuitive Flask-based UI.

## Advantages ✅
- **Automated Data Collection**: Eliminates manual copy-pasting of reviews.
- **Scalable**: Can be extended to scrape more fields or other e-commerce sites.
- **Database Integration**: Efficiently manages data using MongoDB.
- **Modern Tech Stack**: Uses popular libraries like Pandas, Matplotlib, and Flask.

## Disadvantages ❌
- **Dependency on Site Structure**: If Flipkart changes its HTML structure, the scraper locators verify need updates.
- **Performance**: Selenium can be slower than API-based methods (though Flipkart doesn't provide a public review API).
- **IP Blocking Risk**: Frequent requests might lead to temporary IP bans by Flipkart (mitigated by reasonable delays).

## Integration Guide 🔗
The project consists of several modules working together:
1.  **`app.py`**: The Flask application entry point. Handles routes (`/`, `/feedback`, `/graph`) and manages the scraping flow.
2.  **`FlipkratScrapping.py`**: Contains the `FlipkratScrapper` class which uses Selenium to interact with the browser.
3.  **`mongoDBOperations.py`**: Handles all database interactions (CRUD operations) with MongoDB.
4.  **`RepositoryForObject.py`**: (Implicitly used) Stores XPath/CSS selectors to keep the code clean.
5.  **`requirements.txt`**: Lists all Python dependencies.

## Deployment Instructions ☁️

### Local Deployment
1.  **Clone the Repository**:
    ```bash
    git clone <repository-url>
    cd FlipkratScrappingProject
    ```

2.  **Install Dependencies**:
    ```bash
    pip install -r requirements.txt
    ```

3.  **Set Up Environment Variables**:
    Create a `.env` file in the root directory and add your MongoDB credentials:
    ```env
    MONGO_USERNAME=your_username
    MONGO_PASSWORD=your_password
    # OR
    MONGO_URI=your_mongodb_connection_string
    ```

4.  **Run the Application**:
    ```bash
    python app.py
    ```
    The app will start on standard port `8000` (http://localhost:8000).

### Cloud Deployment (Heroku/Render)
1.  **Prepare Files**: Ensure `requirements.txt` and `Procfile` are present.
    - `Procfile` content: `web: gunicorn app:app`
2.  **Set Environment Variables**: In your cloud dashboard, add the `MONGO_URI` (or username/password) variables.
3.  **Buildpacks**:
    - For Selenium, you may need to add Chrome and Chromedriver buildpacks if not using a Docker container.
    - **Heroku Buildpacks**:
        1. `https://github.com/heroku/heroku-buildpack-google-chrome`
        2. `https://github.com/heroku/heroku-buildpack-chromedriver`

## Requirements
- Python 3.8+
- Google Chrome
- MongoDB (Atlas or Local)

## Troubleshooting
- **Selenium Errors**: Ensure your Chrome version matches the specific driver version, or relies on `webdriver-manager` (which this project does automatically).
- **Database Connection**: Check if your IP is whitelisted in MongoDB Atlas.

---
*Created by [Your Name]*
