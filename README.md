# Analyzing Air Quality Index (AQI) and Key Pollutant Trends in Indian Cities Using Power BI

## Table of Contents

- [Project Overview](#project-overview)
- [Data & Methodology](#data-and-methodology)
- [Tools Used](#tools-used)
- [Key Questions Answered](#key-questions-answered)
- [Dashboard Snapshots](#dashboard-snapshots)
- [Notable Insights](#notable-insights)
- [Future Scope of Work](#future-scope-of-work)

## Project Overview

This project features an interactive Power BI report that explores air quality across seven major Indian cities from April 2022 to March 2023. Using real-world AQI data, the report uncovers how major pollutants fluctuate over time—across seasons, months, and even days. It also highlights city-wise AQI performance and identifies the dominant contributors to air pollution in each city. The report includes interactive filters for seamless and user-friendly data exploration.

## Data & Methodology

- **Pollutants Tracked:** PM2.5, PM10, CO, O₃, NO₂, SO₂, NH₃  
- **Cities Covered:** Patna, Lucknow, Chandigarh, Kolkata, Bhopal, Prayagraj (Allahabad), Thiruvananthapuram  
- **Data Collected:** Daily AQI sub-indices for all 7 pollutants are recorded from [CPCB AQI data](https://airquality.cpcb.gov.in/AQI_India/)  
- **Approach:**  
  - The CPCB website provides the values of the sub-indices for each pollutant.  
  - From the sub-indices, concentration (**Concₚ**) values were calculated individually for all pollutants using the reverse AQI formula:  

    ```
    Concₚ = [(AQIₚ - AQILo) * (ConcHi - ConcLo) / (AQIHi - AQILo)] + ConcLo
    ```

    Where:  
     **AQIₚ** is the sub-index of the pollutant.  
     **Concₚ** is the rounded concentration of the pollutant.  
     **ConcHi** is the concentration breakpoint ≥ Concₚ (Upper Limit).  
     **ConcLo** is the concentration breakpoint ≤ Concₚ (Lower Limit).  
     **AQIHi** is the AQI corresponding to ConcHi (Upper Limit).  
     **AQILo** is the AQI corresponding to ConcLo (Lower Limit).  

  - The **overall AQI per city per day** was derived as the **maximum sub-index** of all pollutants.  

- The table below outlines the permissible concentration ranges with respect to each pollutant within the various AQI categories, serving as a reference for interpreting overall air quality during the given time period. There is one more AQI category *“Severe Plus”* with an AQI above 500.



  <p align="center">
<img width="1002" height="467" alt="AQI Table" src="https://github.com/user-attachments/assets/5316798d-e24a-4954-bf27-ebf8fc1487b5" />
</p>

## Tools Used  

- **Microsoft Excel** – for basic data pre-processing  
- **Power BI Desktop** – including **Power Query Editor** (for data shaping and merging) and **DAX** (for custom calculations).  

## Key Questions Answered  

1. What is the average concentration of major air pollutants, as well as the average AQI throughout the year?  
2. How many days did each city fall under different AQI categories (Good, Satisfactory, Moderate, Poor, Very Poor, Severe and Severe Plus)?  
3. Which pollutants are the primary contributors to the overall AQI of each city, and what is their respective percentage contribution?  
4. What are the minimum and maximum AQI levels recorded in each city, and which are the top three pollutants in each case?  
5. How do pollutant concentrations vary across seasons, months, and days? And how do daily concentrations compare to CPCB and WHO standards?  
6. How does the overall AQI trend shift over the course of the year?  

## Dashboard Snapshots

![Image](https://github.com/user-attachments/assets/7714d407-b57a-451f-9383-c97fd333ac27)

![Image](https://github.com/user-attachments/assets/fbf9a542-d0b3-4713-aa9c-58c10b5e4838)

## Notable Insights  

- **Patna (248)** and **Lucknow (200)** recorded the highest average AQI, primarily driven by PM2.5 and PM10, followed by NO₂ and CO.  
- **Thiruvananthapuram (60)** stood out as the cleanest city, with 166 'Good' days, only 1 'Poor' day, and zero 'Very Poor' or 'Severe' days — a clear outlier among all cities.  
- **PM2.5 and PM10** are the dominant pollutants across most cities, jointly contributing to over **63%** of the AQI.  
- Air quality deteriorates sharply from late post-monsoon, with AQI rising from November, peaking in December–January, and declining by February. This trend is driven by elevated winter emissions of most pollutants mainly due to stubble burning, temperature inversion, low wind speeds, and increased fossil fuel use for heating. However, weak winter sunlight keeps ozone levels suppressed, which rises again in summer.  
- This analysis, however, shows an unexpected result: **SO₂ and NO₂ peaking in summer, and NH₃ in winter**, deviating from typical seasonal patterns. It calls for deeper analysis to assess whether these contradictions reflect region-specific seasonal patterns — possibly driven by increased summer activity from vehicles, industries, and thermal power plants leading to higher SO₂ and NO₂ levels, and wintertime ammonia build-up from stubble burning and livestock waste, particularly in the northern states of India — or if they're just occasional spikes.  
- While summer months consistently show **moderate AQI**, September (post-monsoon) mostly falls within the **satisfactory range**, pulling down the seasonal average — so despite November showing **poor to very poor AQI**, post-monsoon ranks below summer in average pollution levels.  

## Future Scope of Work  

- There's room to expand the analysis by including more cities and extending the timeline, which could reveal broader patterns and long-term trends.  
- Adding meteorological factors like temperature and wind speed could uncover stronger links between weather and air quality.
- With Power BI Service, the report can be automatically refreshed each month, keeping the analysis always up to date — no manual uploads needed.  
