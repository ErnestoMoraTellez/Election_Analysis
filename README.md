# Election_Analysis

## Overview of Election Audit
We are helping Tom to determine the winner on Colorado elections. We need to report the Total number of votes, votes for each candidate and the percentage of the candidate votes. Tom's manager wants to automate the process using python.

### Purpose
With the use of python, we want to automate the counting of the votes to determine and certify the winner of the election using this report.

## Election-Audit Result
- How many votes were cast in this congressional election?
To determine the total votes, first we need to import the python library of CSV and OS to access the csv document information. And we create a variable to stock the toal number of votes.

-------------------------------------------------------------------------------------------------------------------------------
    "Add our dependencies.
    import csv
    import os

    "Add a variable to load a file from a path.
    file_to_load = os.path.join("Resources", "election_results.csv")
    "Add a variable to save the file to a path.
    file_to_save = os.path.join("analysis", "election_analysis.txt")

    "Initialize a total vote counter.
    total_votes = 0

    In order to increase the sum of the votes to get the total. We acces to the document with the csv library and with a for loop we navegate through all the rows, adding one by one the votes

    "Read the csv and convert it into a list of dictionaries
    with open(file_to_load) as election_data:
        reader = csv.reader(election_data)

        "Read the header
        header = next(reader)

        "For each row in the CSV file.
        for row in reader:

            "Add to the total vote count
            total_votes = total_votes + 1

-------------------------------------------------------------------------------------------------------------------------------

We get this result when we print the "total_votes" variable. It accumulates all the votes on the different rows of the document.

![image](https://user-images.githubusercontent.com/88845919/135945710-4e8e4c1a-3a9a-4c1f-85ed-c1c37ff43a73.png)

- Provide a breakdown of the number of votes and the percentage of total votes for each county in the precinct.
To determine the number of votes and percetage of total votes of each county, we create diferent variables, one list for the county options, and one dictionary to save the county names with their individual total votes.

-------------------------------------------------------------------------------------------------------------------------------

    "Create a county list and county votes dictionary.

    county_options = []
    county_votes = {}

-------------------------------------------------------------------------------------------------------------------------------

To get the total information about county, we need to count the votes and sum depending on the county. So we use a if statement to add the different county to the list of county_options. We go through all the rows and check if the county already exist in the list, and if not, we add it. Ones we have the county name, we asign a starting value of votes (0 votes). Then we start accumulating one vote for each time that we find the same county in the document.

-------------------------------------------------------------------------------------------------------------------------------

     "4a: Write an if statement that checks that the
            "county does not match any existing county in the county list.
            if county not in county_options:

                "4b: Add the existing county to the list of counties.
                county_options.append(county)

                "4c: Begin tracking the county's vote count.
                county_votes[county] = 0

            "5: Add a vote to that county's vote count.
            county_votes[county] += 1
        
-------------------------------------------------------------------------------------------------------------------------------

Ones we have our list with all the counties and the total votes, we calculate the percentange of it and print the result.

-------------------------------------------------------------------------------------------------------------------------------

    "6a: Write a for loop to get the county from the county dictionary.
    for county  in county_options:
        "6b: Retrieve the county vote count.
        votes = county_votes.get(county)
        "6c: Calculate the percentage of votes for the county.
        vote_percentage = float(votes) / float(total_votes) * 100
        county_results = (
            f"{county}: {vote_percentage:.1f}% ({votes:,})\n")

         "6d: Print the county results to the terminal.
        print(county_results)
         "6e: Save the county votes to a text file.
        txt_file.write(county_results)

-------------------------------------------------------------------------------------------------------------------------------

The final result looks as follows:

![image](https://user-images.githubusercontent.com/88845919/135952558-f6ff84e6-43fb-45cc-aab1-66cfb023f4e4.png)

- Which county had the largest number of votes?
To get the largest number of votes, we just compare with a if statement the actual total votes for each county in the list, and set the higher as the winner.

-------------------------------------------------------------------------------------------------------------------------------

    # 6f: Write an if statement to determine the winning county and get its vote count.
            if (votes > winning_county_count):
                winning_county_count = votes
                winning_county = county

        # 7: Print the county with the largest turnout to the terminal.
        winning_county_summary = (
            f"-------------------------\n"
            f"Largest County Turnout: {winning_county}\n"
            f"-------------------------\n\n")
        print(winning_county_summary)

-------------------------------------------------------------------------------------------------------------------------------

The result looks like this:

![image](https://user-images.githubusercontent.com/88845919/135952822-7c514208-891b-4a94-94a6-32fde8aa9450.png)

- Provide a breakdown of the number of votes and the percentage of the total votes each candidate received.

To determine the differente candidates and votes for each, we use the same method. We look through the document, add to a list all the individual candidates and start counting the votes for each one.

-------------------------------------------------------------------------------------------------------------------------------

    "For each row in the CSV file.
        for row in reader:

            "Add to the total vote count
            total_votes = total_votes + 1

            "Get the candidate name from each row.
            candidate_name = row[2]

            "3: Extract the county name from each row.
            county = row[1]


            "If the candidate does not match any existing candidate add it to
            "the candidate list
            if candidate_name not in candidate_options:

                "Add the candidate name to the candidate list.
                candidate_options.append(candidate_name)

                "And begin tracking that candidate's voter count.
                candidate_votes[candidate_name] = 0

            "Add a vote to that candidate's count
            candidate_votes[candidate_name] += 1


    "Save the final candidate vote count to the text file.
        for candidate_name in candidate_votes:

            "Retrieve vote count and percentage
            votes = candidate_votes.get(candidate_name)
            vote_percentage = float(votes) / float(total_votes) * 100
            candidate_results = (
                f"{candidate_name}: {vote_percentage:.1f}% ({votes:,})\n")

            "Print each candidate's voter count and percentage to the terminal.
            print(candidate_results)

-------------------------------------------------------------------------------------------------------------------------------

The final result looks like this:

![image](https://user-images.githubusercontent.com/88845919/135953310-dac3a589-12bf-45dd-b86c-8ca5ff7e6382.png)

- Which candidate won the election, what was their vote count, and what was their percentage of the total votes?
To determine the winner of the election, we use a if statement to get the person with the higher number of votes, and the higher percentage. Then we print the winner.

-------------------------------------------------------------------------------------------------------------------------------

    "Determine winning vote count, winning percentage, and candidate.
            if (votes > winning_count) and (vote_percentage > winning_percentage):
                winning_count = votes
                winning_candidate = candidate_name
                winning_percentage = vote_percentage

        "Print the winning candidate (to terminal)
        winning_candidate_summary = (
            f"-------------------------\n"
            f"Winner: {winning_candidate}\n"
            f"Winning Vote Count: {winning_count:,}\n"
            f"Winning Percentage: {winning_percentage:.1f}%\n"
            f"-------------------------\n")
        print(winning_candidate_summary)
    
-------------------------------------------------------------------------------------------------------------------------------

The result looks like this:

![image](https://user-images.githubusercontent.com/88845919/135953505-10b0de29-af1b-4efd-8078-c054668ca938.png)

## Election-Audit Summary
