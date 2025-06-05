# Reddit Scraper

A Python-based tool for scraping and analyzing posts from Reddit subreddits. This script collects various metrics about posts including upvotes, comments, timestamps, and more, saving the data to an Excel file for further analysis.

## Prerequisites

- Python 3.12 or higher
- pip (Python package installer)

## Installation

1. Clone this repository or download the files to your local machine.

2. Create a virtual environment (recommended, but optional):
```terminal
python -m venv ms-scraper
source ms-scraper/bin/activate  # On Windows, use: ms-scraper\Scripts\activate
```

3. Install the required packages:
```terminal
pip install -r requirements.txt
```

## Reddit API Authentication

To use this scraper, you'll need to create a Reddit API application:

1. Go to https://www.reddit.com/prefs/apps
2. Click "create another app..." at the bottom of the page
3. Fill in the following details:
   - Name: Choose any name for your application
   - Select "script" as the application type
   - Description: Optional
   - About URL: Optional
   - Redirect URI: Use http://localhost:8080
4. Click "create app"
5. Note down your:
   - Client ID (under the app name)
   - Client Secret (labeled "secret")

## Configuration

Update the authentication details in the script with your Reddit API credentials:

```python
reddit = praw.Reddit(
    client_id="YOUR_CLIENT_ID",
    client_secret="YOUR_CLIENT_SECRET",
    user_agent="script:fetcher:v1.0 (by u/YOUR_USERNAME)"
)
```

Replace:
- `YOUR_CLIENT_ID` with your Reddit API client ID
- `YOUR_CLIENT_SECRET` with your Reddit API client secret
- `YOUR_USERNAME` with your Reddit username (or you can leave this field as it is.)

## Usage

1. Open the Jupyter notebook `MS_Reddit_Scraper.ipynb`
2. Run the cells in sequence
3. The script will:
   - Create a `data` directory if it doesn't exist
   - Scrape posts from the specified subreddit
   - Save the data to an Excel file with timestamp
   - Display summary statistics

## Features

The scraper collects the following data for each post:
- Post ID
- Title
- Content
- Author
- Subreddit information
- URL and permalink
- Creation timestamp
- Number of comments
- Score and upvote/downvote counts
- Upvote ratio
- Post type (self post or link)
- Flair information

## Output

The script generates an Excel file with the following naming convention:
```
data/reddit_metrics_[SUBREDDIT_NAME]_[TIMESTAMP].xlsx
```

The Excel file contains all the collected metrics and summary statistics including:
- Total posts analyzed
- Average upvotes
- Average comments
- Number of posts with links
- Number of posts removed by moderators
- Number of AMA posts

## Rate Limiting

The script includes a random delay (10-30 seconds) between requests to comply with Reddit's API rate limits.

## Notes

- The script currently scrapes the top hot posts from the specified subreddit
- You can modify the `limit` parameter in `subreddit.hot(limit=1)` to scrape more posts
- Be mindful of Reddit's API terms of service and rate limits
- The script creates a new Excel file for each run with a timestamp in the filename

## Troubleshooting

If you encounter any issues:
1. Verify your Reddit API credentials are correct
2. Ensure all required packages are installed
3. Check your internet connection
4. Verify you have write permissions in the directory

## License

This project is open source and available under the MIT License. 