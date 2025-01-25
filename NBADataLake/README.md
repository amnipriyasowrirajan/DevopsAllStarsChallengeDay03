 # NBA Data Lake Project

## Project Overview
This project creates an NBA data lake using AWS services including S3, Glue, Athena, and QuickSight to process and visualize NBA player data.

---

## Prerequisites

1. **Dependencies**:
    - boto3==1.26.137
    - python-dotenv==1.0.0
    - requests==2.28.2

2. **Environment Variables**:
    - `Access Key ID`
    - `Secret Access Key`
    - `Default Region` (e.g., `us-east-1`)
    - `nba_sports_api_key`
    - `NBA_endpoint`

3. Add the above variables to an `.env` file.

---

## Instructions

### Step 1: Setup

1. Create the following folder structure:
   ```
   nbadatalake/
       src/
           nba_datalake.py
           delete.py
   ```

2. Create a `requirements.txt` file with the following content:
   ```
   boto3==1.26.137
   python-dotenv==1.0.0
   requests==2.28.2
   ```

3. Install dependencies by running:
   ```
   pip install -r requirements.txt
   ```

### Step 2: Run the Python Script

1. Execute the script to create necessary resources:
   ```
   python src/nba_datalake.py
   ```
2. Check the created S3 bucket for the `nba_player_data.json` file in the raw data folder.

### Step 3: Query Data with Athena

1. Log in to AWS Athena.
2. Query the data:
   ```sql
   SELECT FirstName, LastName, Position, Team
   FROM nba_players;
   ```
3. Scroll through the query results and download them as a CSV file.

### Step 4: Visualize Data with QuickSight

1. Create a QuickSight account.
2. Connect the S3 bucket containing the CSV file.
3. Upload the CSV file as a new dataset in QuickSight:
   - Go to `Datasets` > `New Dataset` > `Upload a file`.
4. Visualize the data:
   - Create pie charts, bar charts, or any desired visuals.
   - Use appropriate fields for the X-axis and Y-axis.
5. Download or screenshot the charts.

### Step 5: Clean Up

1. Delete the QuickSight account:
   - Go to `Account Settings` > `Manage`.
   - Toggle off termination protection.
   - Type `confirm` to delete the account.
2. Run the cleanup script to remove AWS resources:
   ```
   python src/delete.py
   ```

---

## Additional Notes

- Ensure the S3 bucket name is unique.
- Use the provided NBA API to fetch player data: [Sports Data API](https://sportsdata.io/members/subscriptions).

---

## Outputs

- S3 Bucket with raw data (`nba_player_data.json`).
- Athena database and query results.
- Visualizations in QuickSight (e.g., pie charts, bar charts).

---

## Cleanup Reminder

After completing the project, ensure all AWS resources and accounts are properly deleted to avoid unnecessary charges.


