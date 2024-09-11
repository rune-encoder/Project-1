EV Station Work

#alex_exploration
using data sets from JD Powers and BTS.gov on EV stations in California, Florida, and Texas.

First we take one set, BTS.gov and see what columns exist and what data can be gathered.

We then select columns: State, City, Zip.
We then rename the columns "date", "state", "city", "zip_code"

We sort out the values for date. We need to see if the dates are all in the same type.

We sort out the values for zip codes and make sure they are also in the same type

After we get them sorted out, we then begin using the "Open date" to gather a timeline for when the EV stations were opened. 

We select columns "State","City","ZIP"

We will renam the columns
df.rename(columns={
    "Open Date": "date",
    "State": "state",
    "City": "city",
    "ZIP": "zip_code",
},inplace=True)
df

We will get the zip codes into the same type

df["zip_code"]
zip_code_list = df["zip_code"].unique().tolist()
zip_code_list

def cleaned_zip_code(value):
    if type(value) is int or type(value) is float:
       return str(int(value))
    elif type(value) is str and value.isdigit():
        return value
    elif pd.isna(value):
        return np.nan
    else: 
        return np.nan
    
    
df["zip_code"].apply(cleaned_zip_code)

We are then going to use the Open dates to form the timeline

tx_fuelstation_df = pd.read_csv(
    Path("../../../data/raw_data/TX_2024_alt_fuel_stations (Aug 30 2024)-3.csv"),
    index_col="Open Date",
    parse_dates=True,
)

print("Shape:", tx_fuelstation_df.shape)
tx_fuelstation_df.sort_values("Open Date")

display(tx_fuelstation_df.head())
display(tx_fuelstation_df.tail())



After we have compared BTS.gov stats, we will then compare to JD Powers to see if they are the same data set that can be used. 

#California merging counties
use these codes for Florida merging counties , Texas Merging counties

Will use the merged data for Open dates and zip codes, county to make graphs/charts

from pathlib import Path
import datetime as dt
import pandas as pd
import numpy as np

df_ca = pd.read_csv(Path("../../../data/processed_data/ca_cleaned_ev_stations_data.csv"))

# List of specified counties
specified_counties = ['Los Angeles County', 'San Diego County', 'Orange County', 'Riverside County', 'San Bernardino County']

# Create a new column 'cleaned_county' to store the cleaned county names
df_ca['cleaned_county'] = df_ca['county']

# Replace the county names not in the specified list with 'Other California Counties'
df_ca.loc[~df_ca['county'].isin(specified_counties), 'cleaned_county'] = 'Other California Counties'

# Group by 'year' and 'cleaned_county' and sum the 'ev_station_count' and 'cumulative_ev_stations'
cleaned_df = df_ca.groupby(['year', 'cleaned_county']).sum().reset_index()

# Drop the 'county' column and rename the 'cleaned_county' column back to 'county'
cleaned_df.drop('county', axis=1, inplace=True)
cleaned_df.rename(columns={'cleaned_county': 'county'}, inplace=True)

cleaned_df

# Save the cleaned data to a new CSV file
cleaned_df.to_csv('ca_cleaned_ev_stations_topfive_data.csv', index=False)

import pandas as pd
import matplotlib.pyplot as plt

# Load the data from the CSV file
df_ca_topfive = pd.read_csv(Path("../../../data/processed_data/ca_cleaned_ev_stations_topfive_data.csv"))

df_ca_topfive

# Create a separate plot for each county
counties = ['Los Angeles County', 'San Diego County', 'Orange County', 'Riverside County', 'San Bernardino County', 'Other California Counties']

fig, ax = plt.subplots()
for county in counties:
    county_data = df_ca_topfive[df_ca_topfive['county'] == county]
    ax.plot(county_data['year'], county_data['cumulative_ev_stations'], label=county)

# Add labels and legend
ax.set_xlabel('Year')
ax.set_ylabel('Number of EV Stations')
ax.legend()

# Show the plot
plt.show()

# Create a pie chart to visualize the distribution of 'cumulative_ev_stations' by county for the latest year in the data
latest_year = df_ca_topfive['year'].max()
latest_data = df_ca_topfive[df_ca_topfive['year'] == latest_year]

plt.figure(figsize=(10, 6))
plt.pie(latest_data['cumulative_ev_stations'], labels=latest_data['county'], autopct='%1.1f%%', startangle=140)
plt.axis('equal')  # Equal aspect ratio ensures that pie is drawn as a circle.

plt.title(f'Distribution of Cumulative EV Stations in California by County in {latest_year}')
plt.show()

# Group by 'year' and sum the 'cumulative_ev_stations' for all counties
total_ca_data = df_ca_topfive.groupby('year')['cumulative_ev_stations'].sum().reset_index()

# Plot the progression graph
plt.figure(figsize=(12, 6))
plt.plot(total_ca_data['year'], total_ca_data['cumulative_ev_stations'], marker='o', color='b', linestyle='-')

# Add labels and title
plt.xlabel('Year')
plt.ylabel('Total Number of EV Stations in California')
plt.title('Total EV Stations in California Over the Years')

# Show the plot
plt.grid(True)
plt.show()


Merged State Date EF Openings

Will take the data of the California, Florida, Texas and combine for a progression chart over the years
# Load the data from the .csv files
df_tx_topfive = pd.read_csv(Path("../../../data/processed_data/tx_cleaned_ev_stations_data_topfive.csv"))
df_fl_topfive = pd.read_csv(Path("../../../data/processed_data/fl_cleaned_ev_stations_data_topfive_2.csv"))
df_ca_topfive = pd.read_csv(Path("../../../data/processed_data/ca_cleaned_ev_stations_topfive_data.csv"))

# Merge the cleaned DataFrames for California, Florida, and Texas based on the 'year' column
combined_df = pd.concat([df_tx_topfive,df_fl_topfive,df_ca_topfive])

# Group by 'year' and sum the 'cumulative_ev_stations' for each state
progression_df = combined_df.groupby(['year', 'county']).sum().reset_index()

# Create a progression graph with years on the x-axis and total number of EVs on the y-axis
fig, ax = plt.subplots()
for state in ['California', 'Florida', 'Texas']:
    state_data = progression_df[progression_df['county'].str.contains(state)]
    ax.plot(state_data['year'], state_data['cumulative_ev_stations'], label=state)

# Add labels and legend
ax.set_xlabel('Year') 
ax.set_ylabel('Total Number of EV Stations')
ax.legend()

# Show the progression graph
plt.show()

