import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load the data
data_url = "https://data.cityofnewyork.us/resource/tg4x-b46p.csv"
film_permits = pd.read_csv(data_url)

# Display basic info and preview
print("Data Summary:")
print(film_permits.info())
print(film_permits.head())

# Data Cleaning: Drop rows with missing values in critical columns
film_permits = film_permits.dropna(subset=['EventType', 'StartDateTime', 'EndDateTime'])

# Convert date columns to datetime format
film_permits['StartDateTime'] = pd.to_datetime(film_permits['StartDateTime'])
film_permits['EndDateTime'] = pd.to_datetime(film_permits['EndDateTime'])

# Add a duration column (in hours)
film_permits['DurationHours'] = (film_permits['EndDateTime'] - film_permits['StartDateTime']).dt.total_seconds() / 3600

# Analysis: Top 10 most common event types
top_events = film_permits['EventType'].value_counts().head(10)
print("\nTop 10 Event Types:")
print(top_events)

# Plotting: Top 10 Event Types
plt.figure(figsize=(10, 6))
sns.barplot(x=top_events.values, y=top_events.index, palette='viridis')
plt.title('Top 10 Most Common NYC Film Permit Event Types')
plt.xlabel('Number of Permits')
plt.ylabel('Event Type')
plt.show()

# Analysis: Average duration by event type
avg_duration = film_permits.groupby('EventType')['DurationHours'].mean().sort_values(ascending=False).head(10)
print("\nAverage Duration of Top 10 Event Types (in hours):")
print(avg_duration)

# Plotting: Average Duration of Event Types
plt.figure(figsize=(10, 6))
sns.barplot(x=avg_duration.values, y=avg_duration.index, palette='plasma')
plt.title('Average Duration of Top 10 Event Types (in hours)')
plt.xlabel('Average Duration (hours)')
plt.ylabel('Event Type')
plt.show()

# Save cleaned data to a CSV file
film_permits.to_csv('cleaned_film_permits.csv', index=False)
print("\nCleaned data saved as 'cleaned_film_permits.csv'")
