<img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif">
<div align="center">
  
# JiggleCoord: A geocoding utility for python

<img align="center" alt="GIF" src="https://github.com/ssopic/JiggleCoord/blob/main/main.jpg" width="150px" height="150" />
  
</div><img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif">

## Summary

This package provides a robust solution for reverse geocoding geographical coordinates (**returns the address details in and merges them into a dataframe**), a task often complicated by points falling on administrative boundaries. It intelligently addresses this challenge by employing a "snowflake" perturbation strategy, where it systematically tests nearby coordinates to "escape" the boundary and find a valid, non-ambiguous location. This functionality is seamlessly integrated with pandas DataFrames, allowing for efficient and reliable geocoding of large datasets for data science and analysis.


## Features
- Smart Geocoding: Automatically handles cases where a coordinate falls on a geographical boundary.
- "Snowflake" Perturbation: When a boundary is detected, the package generates a small, structured grid of surrounding points to find the nearest valid location using the Haversine formula.
- DataFrame Integration: Seamlessly processes large datasets by integrating directly with pandas DataFrames.
- Rate-Limited: Uses geopy's built-in rate limiter to respect API usage policies.

## Installation
You can install the package directly from PyPI:

``` pip install JiggleCoord ```

## License
This project is licensed under the MIT License - see the LICENSE file for details.
## Dependencies
- pandas
- geopy

## Quickstart

### Output 

## Under the hood


