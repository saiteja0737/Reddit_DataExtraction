# Reddit_DataExtraction

# Reddit AI Data Collection Pipeline

## Assignment Overview
This project builds a Python application that interfaces with the Reddit API to collect, process, and store social media data from AI-related communities. The pipeline fetches hot posts and performs keyword-based searches across three subreddits, extracting structured data for analysis.

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
1. Create a file named `reddit.env` in the project directory
2. Add your Reddit API credentials in the following format:
```
REDDIT_CLIENT_ID=your_client_id_here
REDDIT_CLIENT_SECRET=your_client_secret_here
REDDIT_USER_AGENT=your_user_agent_here
```
3. Replace the placeholder values with your actual credentials from Reddit's app dashboard

### Execution
Run the main script:
```
python reddit_code.py
```

## Output Description

### reddit_data.csv
The final output file contains 760 unique posts collected from three AI-related subreddits (r/ArtificialInteligence, r/OpenAI, r/AI_Agents).

**Columns (20 total):**

**Required Columns (14):**
- title: Post title
- score: Net score (upvotes - downvotes)
- upvote_ratio: Ratio of upvotes to total votes
- num_comments: Total number of comments
- author: Username of post author
- subreddit: Subreddit where post originated
- url: External URL (if applicable)
- permalink: Permanent Reddit URL
- created_utc: Unix timestamp of creation
- is_self: Boolean indicating text-only post
- selftext: Body text (truncated to 500 characters)
- flair: Category tag assigned to post
- domain: Domain of linked content
- search_query: Keyword used to find post (None for hot posts)

**Additional Columns (6):**
- post_id: Unique post identifier
- total_awards: Number of awards received
- is_nsfw: Content warning flag
- is_locked: Discussion locked by moderators
- is_stickied: Pinned by moderators
- distinguished: Posted by moderator/admin

**Data Distribution:**
- Hot posts: 150 (from Task 1)
- Keyword search posts: 610 (from Task 2)
- Total unique posts: 760 (after deduplication)

**Keywords searched:** ChatGPT, GPT-5, Gemini, Sora, Claude, AI safety, AGI, LLMs, RAG
