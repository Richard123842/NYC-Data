# NYC-Data
analyzing publicly available data on film permits in New York City
NYC Film Permit Data Analysis
Project Overview
This project analyzes publicly available film permit data from New York City to identify trends and insights related to event types and their durations. The analysis leverages Python libraries such as Pandas, Matplotlib, and Seaborn to clean, process, and visualize the data.

Data Source
The dataset is obtained from the official NYC Open Data portal:
NYC Film Permit Data

Features
Data Cleaning: Handles missing values and converts date columns to datetime format.

Data Analysis:

Identifies the top 10 most common event types.

Calculates the average duration of each event type.

Data Visualization:

Bar plots of the most common event types.

Bar plots of the average duration for each event type.

Data Export: Saves the cleaned dataset to a CSV file.

Installation
Clone the repository and install the required packages:

bash
Copy
Edit
git clone https://github.com/yourusername/nyc-film-permit-analysis.git
cd nyc-film-permit-analysis
pip install pandas matplotlib seaborn
Usage
Run the analysis script:

bash
Copy
Edit
python analysis.py
Results
The analysis provides insights into the distribution of event types and their average durations. Visualizations make it easier to understand the most common events and their time requirements.

Example Output
Top 10 Most Common Event Types:

Displays the most frequent types of film permits.

Average Duration of Event Types:

Highlights the average time each event type takes.

Visualizations:

Bar plots showcasing the distribution and average duration.

Cleaned Data
The cleaned dataset is saved as cleaned_film_permits.csv in the project directory.

Technologies Used
Python

Pandas

Matplotlib

Seaborn
