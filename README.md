# Election_Analysis

## Overview of Election Audit
We are helping Tom to determine the winner on Colorado elections. We need to report the Total number of votes, votes for each candidate and the percentage of the candidate votes. Tom's manager wants to automate the process using python.

### Purpose
With the use of python, we want to automate the counting of the votes to determine and certify the winner of the election using this report.

## Election-Audit Result
- How many votes were cast in this congressional election?
To determine the total votes, first we need to import the python library of CSV and OS to access the csv document information. And we create a variable to stock the toal number of votes.

# Add our dependencies.
import csv
import os

# Add a variable to load a file from a path.
file_to_load = os.path.join("Resources", "election_results.csv")
# Add a variable to save the file to a path.
file_to_save = os.path.join("analysis", "election_analysis.txt")

# Initialize a total vote counter.
total_votes = 0

In order to increase the sum of the votes to get the total. We acces to the document with the csv library and with a for loop we navegate through all the rows, adding one by one the votes

# Read the csv and convert it into a list of dictionaries
with open(file_to_load) as election_data:
    reader = csv.reader(election_data)

    # Read the header
    header = next(reader)

    # For each row in the CSV file.
    for row in reader:

        # Add to the total vote count
        total_votes = total_votes + 1

We get this result when we print the "total_votes" variable

![image](https://user-images.githubusercontent.com/88845919/135945710-4e8e4c1a-3a9a-4c1f-85ed-c1c37ff43a73.png)

- Provide a breakdown of the number of votes and the percentage of total votes for each county in the precinct.
To determine the number of votes and percetage of total votes of each county, 

- Which county had the largest number of votes?
- Provide a breakdown of the number of votes and the percentage of the total votes each candidate received.
- Which candidate won the election, what was their vote count, and what was their percentage of the total votes?

## Election-Audit Summary
