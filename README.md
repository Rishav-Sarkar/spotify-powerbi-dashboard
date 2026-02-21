🎧 Spotify Analytics Dashboard – Power BI Project

📌 Project Overview

This project is an end-to-end Spotify Data Analysis Dashboard built using Power BI.
The objective was to transform raw streaming data into meaningful business insights through advanced DAX calculations, data modeling, and interactive visualization design.

The dashboard provides comprehensive analysis of:
 • Song performance
 • Artist dominance
 • Album type distribution
 • Explicit vs Non-explicit segmentation
 • Monthly and yearly popularity trends

The design follows a Spotify-inspired dark theme UI with intuitive navigation and dynamic filtering.

⸻

🎯 Business Objectives
 • Analyze overall streaming performance trends
 • Identify top-performing artists and tracks
 • Compare popularity across album types
 • Evaluate explicit vs non-explicit content distribution
 • Discover seasonality in music releases
 • Perform time-based trend analysis

⸻

🛠 Tools & Technologies
 • Power BI Desktop
 • DAX (Data Analysis Expressions)
 • Power Query (ETL & Data Cleaning)
 • Data Modeling (Star Schema Approach)
 • Interactive Dashboard Design

⸻

📊 Dashboard Features

🔹 KPI Overview
 • Total Songs
 • Total Artists
 • Average Popularity
 • Average Duration (Minutes)

🔹 Artist & Track Analysis
 • Top Artists by Song Count
 • Top Songs by Popularity
 • Dynamic Ranking using DAX
 • Interactive cross-filtering

🔹 Album & Content Segmentation
 • Songs by Album Type (Single / Album / Compilation)
 • Explicit vs Non-Explicit distribution
 • Average Popularity by Album Type

🔹 Time Intelligence Analysis
 • Songs by Year
 • Distinct Songs by Month
 • Average Popularity by Month
 • Rolling 3-Month Popularity Trend

⸻

🧠 DAX Measures Implemented

Below are the core DAX calculations powering the dashboard.

⸻

📊 Core Aggregation Measures

➤ Total Songs

Total Songs = 
COUNT('Spotify'[track_id])

➤ Total Artists

Total Artists = 
DISTINCTCOUNT('Spotify'[artist_name])

➤ Average Popularity

Average Popularity = 
AVERAGE('Spotify'[popularity])

➤ Total Duration (Minutes)

Total Duration (Min) = 
DIVIDE(
    SUM('Spotify'[duration_ms]),
    60000
)


📈 Ranking Measures

➤ Artist Popularity Rank

Artist Popularity Rank = 
RANKX(
    ALL('Spotify'[artist_name]),
    [Average Popularity],
    ,
    DESC,
    DENSE
)

➤ Track Popularity Rank

Track Popularity Rank = 
RANKX(
    ALL('Spotify'[track_name]),
    [Average Popularity],
    ,
    DESC,
    DENSE
)


📅 Time Intelligence Measures

(Requires a Calendar table with proper relationships)

➤ Songs YTD

Songs YTD = 
TOTALYTD(
    [Total Songs],
    'Calendar'[Date]
)

➤ Songs Per Month

Songs Per Month = 
CALCULATE(
    [Total Songs],
    ALLEXCEPT('Calendar', 'Calendar'[Month])
)

➤ Rolling 3-Month Popularity

Rolling 3M Popularity = 
CALCULATE(
    [Average Popularity],
    DATESINPERIOD(
        'Calendar'[Date],
        MAX('Calendar'[Date]),
        -3,
        MONTH
    )
)


🎵 Content & Segmentation Measures

➤ Explicit Songs

Explicit Songs = 
CALCULATE(
    [Total Songs],
    'Spotify'[explicit] = TRUE()
)

➤ Non-Explicit Songs

Non Explicit Songs = 
CALCULATE(
    [Total Songs],
    'Spotify'[explicit] = FALSE()
)

➤ Explicit Percentage

Explicit % = 
DIVIDE(
    [Explicit Songs],
    [Total Songs]
)


📀 Album Type Analysis

➤ Songs by Album Type

Songs By Album Type = 
COUNT('Spotify'[album_type])

➤ Average Popularity by Album Type

Average Popularity By Album Type = 
CALCULATE(
    AVERAGE('Spotify'[popularity]),
    VALUES('Spotify'[album_type])
)

📈 Key Insights Derived
 • Singles demonstrate higher average popularity compared to full albums.
 • Non-explicit tracks dominate overall distribution.
 • A small group of artists contributes disproportionately to total song volume.
 • Monthly popularity trends show seasonal variations.
 • Recent releases remain competitive compared to prior years.

⸻

🗂 Data Modeling Approach
 • Implemented Star Schema design
 • Separate Calendar table for time intelligence
 • Fact table: Spotify Tracks
 • Dimension tables: Artists, Calendar

Optimized relationships ensure accurate filter context and performance.

🚀 How to Use
 1. Download the .pbix file
 2. Open using Power BI Desktop
 3. Use slicers and filters to explore interactive insights

⸻

📚 Learning Outcomes

Through this project, I strengthened my skills in:
 • Advanced DAX calculations
 • Time Intelligence functions
 • Data modeling & relationships
 • Performance optimization
 • Business storytelling with data
 • Dashboard UI/UX design principles

⸻

👤 Author

Rishav S.
Aspiring Data Analyst | Power BI & DAX Enthusiast
Focused on building business-driven analytics solutions.

