<a name="readme-top"></a>

<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/madiwiebe/LHL_Capstone_Project">
    <img src="images/wind_turbines_image.jpg" alt="Logo" width="240" height="240">
  </a>

<h1 align="center">Wind or Solar?</h3>

  <p align="center">
    Taking Renewable Energy Home in Any Climate.
  </p>
</div>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#key-findings">Key Findings</a></li>
        <li><a href="#data-considerations">Data Considerations</a></li>
        <li><a href="#tech-stack">Tech Stack</a></li>
      </ul>
    </li>
    <li>
      <a href="#process">Process</a>
      <ul>
        <li><a href="#data-acquisition">Data Acquisition</a></li>
        <li><a href="#data-cleaning-and-eda">Data Cleaning and EDA</a></li>
        <li><a href="feature-engineering">Feature Engineering</li>
        <li><a href="visualizations-and-forecasting">Visualizations and Forecasting< /li>
      </ul>
    </li>
    <li><a href="#results">Results</a></li>
    <li><a href="#challenges">Challenges</a></li>
    <li><a href="#future-goals">Future Goals</a></li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->
## About the Project

Renewable energy is an ever-growing technology sector. As renewable energy options become more accessible to residential settings, homeowners face a decision: which form of energy production is best suited for their home?

This project used historic climate data for the province of BC, Canada to estimate annual energy production potential from wind or solar resources for a given region. 
Solar radiation ($W/{m^2}$) and wind speed ($m/s$) were the key variables used to calculate average solar energy produced over time (kWh) and average wind energy produced over time (kWh). 

<!-- KEY FINDINGS -->
### Key Findings
Overall, wind and solar energy were found to have comparable maximum values for annual energy generation potential.

The region with the highest wind energy potential was the Cariboo region (2,942 kWh / year). The region with the lowest wind energy potential was the Prince George region (470 kWh / year).

The region with the highest solar energy potential was the Northeast region (2,819 kWh / year). The region with the lowest solar energy potential was the Vancouver Island / Coastal region (1,843 kWh / year).

Although both wind and solar energy potential demonstrated highly seasonal trends, both were predicted to produce consistent annual averages over time for a given region.

<!-- DATA CONSIDERATIONS -->
### Data considerations: 
- Wind data included a larger number of observations from a higher number of weather stations, and all regions were represented.
- Solar data had fewer observations from a smaller number of weather stations, and not all regions were represented.
- Wind energy had larger timescale (more data over a longer period of time), and had wider range between the maximum values and the minimum values. 

To achieve a more realistic representation of energy production potential and provide a more reliable basis of comparison, more data must be collected and standardized.

<!-- TECH STACK -->
### Tech stack:
- Python
- Pandas
- Postgres / pgAdmin 4
- Tableau

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- PROCESS -->
## Process
<!-- DATA ACQUISITION -->
### Data Acquisition
- Dataset was downloaded from the [Pacific Climate Data Consortium](https://services.pacificclimate.org/met-data-portal-pcds/app/#close)
- Weather station metadata downloaded separately

<!-- DATA CLEANING AND EDA -->
### Data cleaning and EDA
- Extract wind and solar data from weather station files
- Create a separate file for each 
- Filter for relevant columns
  - wind speed ($m/s$)
  - solar radiation ($W/{m^2}$)
- Standardize column names
  - units
  - handling whitespace
- Remove rows with null values in wind speed or solar radiation
- Remove data with observations outside of a reasonable range

<!-- FEATURE ENGINEERING -->
### Feature engineering
- Create columns for Network ID and Station ID
- Create calculated columns for wind energy and solar energy
- Calculate daily averages for each weather station
- Calculate annual averages for each weather station
- Assign weather stations to regional groups (ignoring network provider)

<!-- VISUALIZATIONS AND FORECASTING -->
### Visualizations and forecasting
- Weather station mapping
  - Distribution
  - Observation frequency
  - Calculated energy production over time
- Regional energy production
  - Calculated energy production over time
  - Predicted energy production over time

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- RESULTS -->
## Results

The results of this project are primarily descriptive, and are intended to lay the groundwork for more detailed analysis with more comprehensive data. 

Key insights relate to average energy production over time, energy production by energy source, and regional trends.

### Question 1: What is the average annual wind energy potential of each region?

### Question 2: What is the average annual solar energy potential of each region?

### Question 3: Which regions have the highest energy potential for each renewable resource?

### Question 4: How does the energy potential for each resource change over time? How much impact does seasonality have on each resource's energy potential?

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CHALLENGES -->
## Challenges 

- Integrating data from 10 distinct weather station networks posed several challenges. Normalizing measurement units, variable names, observation frequencies, and date ranges were all elements that needed significant effort.
- The size of the dataset limited the efficiency of any data transformations. Memory limitations inherent to Pandas as well as computer processing ability made for very incremental cleaning and EDA.
- Large gaps in weather station locations leads to a lack of detailed analysis in remote regions (which are arguably the most relevant target group for homeowners looking for renewable, off-grid energy solutions).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- FUTURE GOALS -->
## Future Goals

- Combine data from other weather resources to improve location coverage.
- Improve consistency in the sample sizes used to calculate energy at a given time.
- Incorporate functions capable of handling dynamic variables instead of set values.
  - number of solar panels
  - solar panel efficiency
  - wind turbine blade length
  - air density (which is itself dependent on air temperature, air pressure, relative humidity, and elevation) 
- Explore Tableau/Python integration (TabPy).
  - Access Tableau calculated fields and LOD expressions with Python libraries.
  - Visualize more complex modeling results in Tableau.
- Develop regression model (decision tree) that uses a target energy production threshold to recommend whether wind, solar, both, or neither are capable of meeting that threshold.
- Create a user interface that allows a client to input their location and receive results based on data from the nearest weather station(s).

<p align="right">(<a href="#readme-top">back to top</a>)</p>
