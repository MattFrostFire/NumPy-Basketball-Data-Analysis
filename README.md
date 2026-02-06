# NumPy-Basketball-Data-Analysis
The purpose of this project is to perform numeric data analysis on real-world basketball player statistics using Python and NumPy. The dataset comes from a Kaggle repository containing player statistics across multiple leagues and seasons.
This project demonstrates how NumPy ndarrays can be used to efficiently manipulate and analyze large datasets.

Dataset and Data Handling

The dataset used in this project contained inconsistencies typical of real-world CSV files, such as:

  Quoted commas in player names (e.g., “Tim Hardaway, Jr.”)
  
  Missing values
  
  Mixed data types within columns
  
  Inconsistent column formatting

Because NumPy’s genfromtxt function cannot reliably parse CSV files with these issues, Pandas was used solely for data ingestion. After reading the CSV file, all relevant columns were converted into NumPy ndarrays, and all calculations were performed using NumPy.

This approach ensures robust data loading while still meeting the requirement of performing analysis with NumPy.

Class Design and Implementation

The program is built around a single class:

BasketballStatsAnalyzer

This class is responsible for:

  Loading and preparing the data
  
  Calculating all required statistical metrics
  
  Ranking the top 100 player-seasons for each metric
  
  This object-oriented design keeps the code organized, readable, and reusable.
  
  Class Attributes

Each attribute stores a NumPy ndarray extracted from the dataset:

Attribute	Description
players	Player names
seasons	Season for each record
games	Games played (GP)
minutes	Minutes played (MIN)
fgm, fga	Field goals made and attempted
tpm, tpa	Three-pointers made and attempted
ftm, fta	Free throws made and attempted
points	Total points scored
blocks	Total blocks
steals	Total steals

All numeric attributes are stored as floating-point NumPy arrays to allow safe mathematical operations.

Class Methods
calculate_metrics()

This method computes the following metrics for each player in each season:

  Field Goal Accuracy
  
  Three Point Accuracy
  
  Free Throw Accuracy
  
  Points Per Minute
  
  Overall Shooting Accuracy
  
  Blocks Per Game
  
  Steals Per Game

np.divide() is used with safeguards to prevent division-by-zero errors, making the program robust against missing or zero values.

The method returns a dictionary mapping metric names to NumPy arrays of calculated values.

get_top_100_rankings(metrics_dict)

This method:
  
  Sorts each metric using np.argsort
  
  Selects the top 100 values
  
  Returns a structured dictionary containing:
  
  Player name
  
  Season
  
  Metric value

This allows easy printing and interpretation of the top performers for each statistic.

Limitations

  The dataset contains missing and inconsistent data which required careful handling during import.
  
  Some player-season records have zero attempts (e.g., no three-point attempts), which results in accuracy values of 0.
  
  Only the statistics required for the assignment were extracted from the dataset.
  
  How to Run the Program
  
  Ensure players_stats_by_season_full_details.csv is in the same folder as the notebook or script.
  
  Run the notebook or Python file.
  
  The program will display the top 100 player-season performances for each metric.

Summary

This project demonstrates:

  Real-world data cleaning considerations
  
  Effective use of NumPy for large-scale numerical analysis
  
  Object-oriented design for clarity and organization
  
  Robust handling of edge cases and malformed data
  
  The combination of Pandas for ingestion and NumPy for computation provides both reliability and performance.
