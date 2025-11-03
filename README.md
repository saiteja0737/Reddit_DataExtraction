# Reddit AI Data Collection Pipeline

## Assignment Overview
This project builds a Python application that interfaces with the Reddit API to collect, process, and store social media data from AI-related communities. The pipeline fetches hot posts and performs keyword-based searches across three subreddits, extracting structured data for analysis.

## Project Workflow

This project follows a structured three-task approach:

### Task 1: Hot Posts Collection
- Collected 50 "hot" (currently trending) posts from each of three AI-related subreddits:
  - **r/ArtificialInteligence** - General AI discussions and trends
  - **r/OpenAI** - Focus on OpenAI products and developments
  - **r/AI_Agents** - Emerging autonomous AI agents technology
- Extracted 20 data fields per post (14 required + 6 additional)
- Implemented error handling for missing values (stored as NaN/None)
- Total collected: 150 hot posts

### Task 2: Keyword-Based Search
- Implemented search functionality across the same three subreddits
- Searched for 9 trending AI keywords:
  - **AI Models**: ChatGPT, GPT-5, Gemini, Sora, Claude
  - **Technical Concepts**: LLMs (Large Language Models), RAG (Retrieval Augmented Generation)
  - **Important Topics**: AI safety, AGI (Artificial General Intelligence)
- Retrieved up to 25 posts per keyword per subreddit
- Populated search_query column for traceability
- Total collected: 667 search posts

### Task 3: Data Processing and Export
- Combined hot posts and search posts into unified dataset (817 total posts)
- Removed 57 duplicate posts based on post_id and permalink
- Final clean dataset: 760 unique posts
- Exported to CSV format without index column
- Maintained consistent schema across all data sources

## How to Run

### Prerequisites
- Python 3.8 or higher
- Reddit API credentials (Client ID, Client Secret, User Agent)
- Google account (if using Google Colab)

### Installation
Install required dependencies:
```
pip install -r requirements.txt
```

### Configuration
1. Create a file named [`REDDIT_API.env`](REDDIT_API.env) in the project directory
2. Add your Reddit API credentials in the following format:
```
REDDIT_CLIENT_ID=your_client_id_here
REDDIT_CLIENT_SECRET=your_client_secret_here
REDDIT_USER_AGENT=your_user_agent_here
```
3. Replace the placeholder values with your actual credentials from Reddit's app dashboard (https://www.reddit.com/prefs/apps)

### Execution

**Option 1: Run Python Script (Direct)**
```
python Reddit_DataExtraction.py
```
**Option 2: Google Colab**
1. Upload [`Reddit_DataExtraction.ipynb`](Reddit_DataExtraction.ipynb) to Google Colab
2. Mount your Google Drive
3. Update the file paths in the notebook to match your Drive structure
4. Ensure `REDDIT_API.env`(REDDIT_API.env) file is in the correct directory
5. Run all cells sequentially

**Option 2: Local Jupyter Notebook**
```
jupyter notebook Reddit_DataExtraction.ipynb
```
Then run all cells in order.

**Note**: Ensure your `reddit.env` file is in the correct directory before running.

## Output Description

### reddit_data.csv
The final output file contains 760 unique posts collected from three AI-related subreddits (r/ArtificialInteligence, r/OpenAI, r/AI_Agents).

**Columns (20 total):**

**Required Columns (14):**
- **title**: Post title
- **score**: Net score (upvotes - downvotes)
- **upvote_ratio**: Ratio of upvotes to total votes
- **num_comments**: Total number of comments
- **author**: Username of post author
- **subreddit**: Subreddit where post originated
- **url**: External URL (if applicable)
- **permalink**: Permanent Reddit URL
- **created_utc**: Unix timestamp of creation
- **is_self**: Boolean indicating text-only post
- **selftext**: Body text (truncated to 500 characters)
- **flair**: Category tag assigned to post
- **domain**: Domain of linked content
- **search_query**: Keyword used to find post (None for hot posts)

**Additional Columns (6):**
- **post_id**: Unique post identifier
- **total_awards**: Number of awards received
- **is_nsfw**: Content warning flag
- **is_locked**: Discussion locked by moderators
- **is_stickied**: Pinned by moderators
- **distinguished**: Posted by moderator/admin

**Data Distribution:**
- Hot posts: 150 (from Task 1)
- Keyword search posts: 610 (from Task 2)
- Total unique posts: 760 (after deduplication)

**Keywords searched:** ChatGPT, GPT-5, Gemini, Sora, Claude, AI safety, AGI, LLMs, RAG

## Project Structure
```
├── [Reddit_DataExtraction.py](Reddit_DataExtraction.py)          # Main Python script
├── [Reddit_DataExtraction.ipynb](Reddit_DataExtraction.ipynb)    # Jupyter notebook version (with outputs)
├── [REDDIT_API.env](REDDIT_API.env)                              # Environment file template
├── [requirements.txt](requirements.txt)                          # Python dependencies
├── [reddit_data.csv](reddit_data.csv)                            # Output dataset (760 posts)
└── [README.md](README.md)                                        # This file
```

## Technologies Used
- **PRAW** (Python Reddit API Wrapper) - Reddit API integration
- **pandas** - Data manipulation and CSV export
- **python-dotenv** - Secure credential management
