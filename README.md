# NYC Airbnb Listing Analysis & Price Exploration 🗽

This project explores the New York City Airbnb Open Data from Kaggle (2019) to understand pricing patterns, popular neighborhoods, availability trends, and the factors influencing listing prices. The analysis involves data cleaning, exploratory data analysis (EDA) using Python, and visualization suggestions for Tableau.

## Project Goal

The main goal was to dive into the NYC Airbnb market data to answer questions like:
* Which boroughs and neighborhoods are most popular/expensive?
* What's the distribution of room types?
* How do factors like location, room type, availability, and reviews correlate with price?
* Are there any interesting patterns related to listing names or review dates?

The cleaned dataset generated from the Python analysis serves as the foundation for building an interactive dashboard in Tableau.

## Data

The primary dataset used is from the `dgomonov/new-york-city-airbnb-open-data` dataset on Kaggle, specifically the `AB_NYC_2019.csv` file. The data is downloaded directly using the `kagglehub` library within the Python notebook. It contains listing details including:
* Listing ID, Name, Host ID, Host Name
* Location: `neighbourhood_group` (Borough), `neighbourhood`, `latitude`, `longitude`
* Listing Details: `room_type`, `price`, `minimum_nights`, `availability_365`
* Reviews: `number_of_reviews`, `last_review`, `reviews_per_month`

## Methodology

1.  **Data Loading & Initial Cleaning (Python - Pandas):**
    * Loaded the dataset.
    * Handled missing values, particularly in `reviews_per_month` (filled with 0) and considered the implications for `last_review`.
    * Checked basic data types and summary statistics.

2.  **Exploratory Data Analysis (Python - Pandas, Matplotlib, Seaborn):**
    * Visualized the distribution of key numerical features like `price` and `availability_365`.
    * Analyzed the frequency of categorical features like `neighbourhood_group` and `room_type`.
    * Investigated relationships between price, location, room type, and reviews using box plots, count plots, and scatter plots.
    * Briefly explored potential outliers in the `price` column.

3.  **Feature Engineering (Python - Pandas):**
    * Created a `days_since_last_review` feature based on the `last_review` date to quantify recency.
    * *Note:* More complex text analysis on `name` or geospatial analysis could be future additions.

4.  **Data Export (Python - Pandas):**
    * Saved the cleaned and slightly feature-engineered DataFrame to `output/nyc_airbnb_cleaned.csv`.

5.  **Visualization (Tableau):**
    * Connected the `nyc_airbnb_cleaned.csv` file to Tableau.
    * **Suggested Dashboards/Visualizations:**
        * An interactive map showing listing density and average price by neighborhood.
        * Price distribution views (histograms/box plots) filterable by borough and room type.
        * Analysis of availability (`availability_365`) patterns.
        * Scatter plots exploring correlations (e.g., price vs. number of reviews).

## Key Findings (Example - Fill with your own!)

* Manhattan has the highest concentration of listings and generally the highest prices, particularly for "Entire home/apt".
* Brooklyn is the second most popular borough.
* The vast majority of listings have prices under $300, but the distribution has a long tail with some very expensive outliers.
* "Entire home/apt" is significantly more expensive than "Private room" or "Shared room".
* (Add more findings based on your specific EDA and Tableau visualizations).

## How to Run

1.  **Clone the repository:**
    ```bash
    git clone <your-repo-url>
    cd nyc-airbnb-analysis
    ```
2.  **Set up Kaggle API Token:** Ensure you have your `kaggle.json` file configured correctly on your system so `kagglehub` can authenticate. See [Kaggle API Credentials](https://github.com/Kaggle/kaggle-api#api-credentials).
3.  **Set up Python environment:**
    ```bash
    pip install -r requirements.txt
    ```
4.  **Run the Jupyter Notebook:** Open and run `nyc_airbnb_analysis.ipynb`. The notebook will automatically download the dataset using `kagglehub`, perform the analysis, and generate the `output/nyc_airbnb_cleaned.csv` file.
5.  **Visualize in Tableau:** Open Tableau Desktop, connect to the `output/nyc_airbnb_cleaned.csv` file, and build your visualizations.
   
## Tools Used

* **Python:** Pandas, NumPy, Matplotlib, Seaborn
* **Tableau Desktop** (for visualization)
* **Jupyter Notebook**
