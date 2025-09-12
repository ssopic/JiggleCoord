<img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif">
<div align="center">
  
# JiggleCoord: A geocoding utility for python

<img align="left" alt="GIF" src="https://github.com/ssopic/JiggleCoord/blob/main/main.jpg" width="150px" height="150" />
  
</div><img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif">


## Features
- Smart Geocoding: Automatically handles cases where a coordinate falls on a geographical boundary.
- "Snowflake" Perturbation: When a boundary is detected, the package generates a small, structured grid of surrounding points to find the nearest valid location using the Haversine formula.
- DataFrame Integration: Seamlessly processes large datasets by integrating directly with pandas DataFrames.
- Rate-Limited: Uses geopy's built-in rate limiter to respect API usage policies.

## Installation
You can install the package directly from PyPI:

pip install JiggleCoord

## License
This project is licensed under the MIT License - see the LICENSE file for details.
## Dependencies
- pandas
- geopy

## Quickstart



## Under the hood


