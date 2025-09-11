Location Helper: A Geocoding Utility for Python
A Python package designed to reliably reverse geocode coordinates, using a smart "snowflake" perturbation strategy to resolve boundary-related errors and return accurate location data.

Features
Smart Geocoding: Automatically handles cases where a coordinate falls on a geographical boundary.

"Snowflake" Perturbation: When a boundary is detected, the package generates a small, structured grid of surrounding points to find the nearest valid location.

DataFrame Integration: Seamlessly processes large datasets by integrating directly with pandas DataFrames.

Rate-Limited: Uses geopy's built-in rate limiter to respect API usage policies.

Installation
You can install the package directly from PyPI:

pip install your-package-name

Quick Start
Here is a simple example demonstrating how to use the geopy_df_geocoder function to geocode a DataFrame. We'll include a coordinate that is intentionally on a boundary to showcase the perturbation feature.

import pandas as pd
from your_package_name import geopy_df_geocoder

# Create a sample DataFrame with coordinates
data = {
    'city_id': [1, 2],
    'latitude': [51.5074, 49.0000],  # London, UK
    'longitude': [-0.1278, 8.0000]   # Near the border between Germany and France
}
df = pd.DataFrame(data)

print("Original DataFrame:")
print(df)
print("\n" + "="*30 + "\n")

# Geocode the DataFrame. The second coordinate will trigger the perturbation.
result_df = geopy_df_geocoder(
    df,
    latitude_col='latitude',
    longitude_col='longitude',
    # Optionally, you can specify when to perturb.
    # geocode_on="class == 'boundary' and type == 'administrative'",
    perturb_levels=1,
    perturb_distance=100
)

print("\nGeocoded DataFrame:")
print(result_df)

Expected Output:

The output will show a new DataFrame with additional columns containing the geocoding results, including a perturbation_layer column that indicates whether the snowflake strategy was used.

Original DataFrame:
   city_id  latitude  longitude
0        1   51.5074    -0.1278
1        2   49.0000     8.0000

==============================

Initial lookup for 49.0000, 8.0000 failed or returned a boundary. Attempting snowflake perturbation...
Testing snowflake coordinate: 49.00000089833503, 8.000000000000002
... (more lines for each test)
Found non-boundary location at perturbation layer 1.
Geocoding complete. The original DataFrame has been updated with new geocoded columns.

Geocoded DataFrame:
   city_id  latitude  longitude  status  perturbation_layer  ...
0        1   51.5074    -0.1278  Success                   0  ...
1        2   49.0000     8.0000  Success                   1  ...

How It Works
The package utilizes the geopy library to perform reverse geocoding. If the initial API response indicates the coordinate is a 'boundary', it intelligently generates a new set of coordinates in eight cardinal and intercardinal directions, at a specified distance. It then iteratively geocodes these new points until a non-boundary location is found, effectively "escaping" the ambiguous area.

License
This project is licensed under the MIT License - see the LICENSE file for details.

Dependencies
pandas

geopy
