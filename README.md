
#🚗 DealSniper: Used Car Market Valuation Engine
**Role:** Machine Learning Engineer / Data Engineer
**Tech Stack:** Python, PostgreSQL, Scikit-Learn, XGBoost, Streamlit, Docker

## 1. The Core Problem (Why I Built This). If you spend any time on Facebook Marketplace or Kijiji looking for a decent used car, you know the frustration. The really good deals—the ones that are genuinely underpriced—get sold within the hour. It's a race against professional flippers and small dealers who are constantly monitoring. My goal here was simple: build a tool that monitors the market 24/7 so I stop missing out on the best listings.

## 2. The Solution (What the App Does)**DealSniper** is an automated pipeline that takes the guesswork out of car hunting. It essentially acts as a smart filter:

1. **Ingests Listings:** It automatically pulls new listing data (price, mileage, year, etc.) from local marketplaces on a set schedule.
2. **Calculates True Value:** It uses regression models to predict the precise market price for any specific vehicle (e.g., a 2018 Honda Civic with 75,000 km).
3. **Finds the Deals:** It flags and alerts me instantly when a car is listed at **15% or more below** its calculated market value.

## 3. Architecture (The Technical Breakdown)* **Data Scrapers:** Custom Python scripts (running on a time schedule) to grab raw listing data.
* **Database:** **PostgreSQL** is used for persistent storage. This is where we build up our historical dataset to map the vehicle depreciation curve over months.
* **Inference Engine:** **XGBoost Regressor** is the core model, trained on rolling 30-day windows of price data to maintain accuracy as the market shifts.
* **User Interface (UI):** A **Streamlit Dashboard** that visualizes the current market trends and provides a clean list of "Live Deals" as soon as they are found.

## 4. Usage (How to Run It)This assumes you're running within the project's activated virtual environment (`venv`).

* `make scrape`: Triggers a new ingestion cycle to fetch fresh data.
* `make train`: Retrains the core valuation model on the latest data we have stored.
* `make app`: Launches the DealSniper dashboard in your web browser.