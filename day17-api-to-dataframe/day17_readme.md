# 1. Title
**API Data Gathering: Building a Movie Dataset from TMDB API**

## 2. Overview
This session (Day 17) is the third installment in the Data Gathering series, following CSV and JSON/SQL. It covers fetching data from a website's API and converting it into a Pandas DataFrame. 

The speaker first explains what an API is conceptually (using an IRCTC/MakeMyTrip train-booking analogy and a Facebook multi-platform analogy). Then, they walk through a full mini-project: building an ~8,551-row, 7-column movie dataset by looping through 429 pages of the TMDB (The Movie DB) "Top Rated Movies" API, converting each page's JSON response into a DataFrame, appending all pages together, and exporting the result to CSV — with a closing note on uploading such self-built datasets to Kaggle.

## 3. Detailed Notes

### 3.1 What Is an API?
- **Definition:** API stands for Application Programming Interface. It allows two pieces of software to talk to each other — connecting two software systems. APIs are essentially data pipelines that carry information from Point A to Point B.
- **Why APIs matter today:** Since virtually everything today runs through some kind of app, APIs are essential to making those apps function.

**Analogy 1 — Railway/Flight Booking (IRCTC, MakeMyTrip, Yatra.com):**
- These are separate companies with separate databases. MakeMyTrip can check IRCTC seat availability without accessing the raw database because IRCTC exposes an API. Calling the API with the right inputs returns a JSON response indicating availability.

**Analogy 2 — Facebook (multi-platform apps):**
- Facebook's software runs on the web, Android, and iOS, all backed by a single database. Every platform interacts with the same database through APIs, keeping them synchronized.

### 3.2 The Goal for This Session
Build a Pandas DataFrame of movie data by hitting the TMDB API's "Top Rated Movies" endpoint, resulting in a dataset with:
- 8,551 rows (movies)
- 7 columns: `id`, `title`, `release_date`, `overview`, `popularity`, `vote_average`, `vote_count`

### 3.3 Step 1: Getting an API Key
- Go to `developers.themoviedb.org` (TMDB's developer site).
- Create an account and retrieve your personal API key from the Settings → API section.
- **Important note:** Don't use someone else's API key. Keys have rate limits, and sharing can lead to issues.

### 3.4 Step 2: Understanding the Raw API Response (JSON)
- Hitting the API URL returns raw JSON data, not a normal webpage.
- Use a "JSON Viewer" tool online to see it in a structured, readable tree format.
- The JSON response is a dictionary with four key-value pairs:
  - `page`: current page number.
  - `results`: a list of dictionaries, each representing one movie.
  - `total_pages`: 428.
  - `total_results`: 8,551.

### 3.5 Step 3: Planning the Target DataFrame
Before writing extraction code, manually decide which fields to keep for each movie.
The plan is to run an extraction process in a loop, once per page (428 times), appending the resulting mini-DataFrames (20 movies per page) to a cumulative DataFrame.

### 3.6 Step 4: Coding — Single-Page Extraction
**Import libraries:**
```python
import pandas as pd
import requests
```

**Make the API request:**
```python
response = requests.get('<TMDB top-rated movies URL with API key and page=1>')
```
- A status code of 200 means success (404 = not found, 500 = server error).

**Convert response to JSON and extract results:**
```python
data = response.json()
results = data['results']
```

**Convert directly into a DataFrame and select desired columns:**
```python
df = pd.DataFrame(results)[['id', 'title', 'overview', 'release_date', 'popularity', 'vote_average', 'vote_count']]
```

### 3.7 Step 5: Scaling Up — Looping Through All 428 Pages
**Create an empty DataFrame to accumulate results:**
```python
df = pd.DataFrame()
```

**Loop through all pages (1 to 428):**
```python
for i in range(1, 429):
    response = requests.get(f'<TMDB URL with page={i}>')
    temp_df = pd.DataFrame(response.json()['results'])[['id', 'title', 'overview', 'release_date', 'popularity', 'vote_average', 'vote_count']]
    df = df.append(temp_df, ignore_index=True)
```
- **F-string:** Used to substitute the loop variable `i` into the URL.
- **`ignore_index=True`:** Crucial for maintaining continuous, clean indexing in the combined DataFrame, avoiding repeated 0-19 indices.

### 3.8 Step 6: Verifying and Exporting the Final Dataset
**Check the shape:**
```python
df.shape
```
- Result: exactly 8,551 rows and 7 columns.

**Export to CSV:**
```python
df.to_csv('movies.csv')
```

### 3.9 Step 7: Uploading Self-Built Datasets to Kaggle
- Self-built datasets can be uploaded to Kaggle to increase visibility on your profile.
- This activity can lead to becoming a recognized "Kaggle Expert" and open up internship opportunities.

### 3.10 Step 8: Finding More APIs to Practice With
- **RapidAPI** is recommended as a resource containing a large, free list of APIs across many categories (sports, weather, flights, etc.).
- Active practice is strongly encouraged to reinforce learning.

## 4. Key Concepts
- An API is an interface that lets two separate pieces of software share specific information securely, without exposing the underlying raw database.
- API responses are typically returned in JSON format, which mirrors Python dictionary/list structures and parses easily into Pandas DataFrames.
- Building a full dataset from a paginated API requires looping through all available pages and accumulating results using `ignore_index=True`.
- Publishing self-built datasets on Kaggle builds a strong public profile.

## 5. Important Definitions
- **API (Application Programming Interface):** A mechanism that allows two software systems to communicate.
- **API Key:** A credential required to authenticate and make requests to an API.
- **JSON (JavaScript Object Notation):** The typical format in which API responses are returned.
- **requests library:** A Python library used to make HTTP requests (e.g., `requests.get()`).
- **Response Status Code:** A number indicating the outcome of a request (200 = OK).
- **response.json():** A method used to parse raw API response content into Python dictionaries.
- **RapidAPI:** A website providing access to a large collection of free (and paid) APIs.

## 6. Algorithms / Workflows

### Workflow: Building a Dataset from a Paginated API
1. **Identify the API and obtain credentials:** Get an API key from the developer site.
2. **Understand the raw response structure:** Hit the URL and use a JSON Viewer to identify key fields.
3. **Plan your target DataFrame:** Decide which JSON keys you need as columns.
4. **Write single-page extraction code:**
   - Use `requests.get(url)`.
   - Parse with `.json()`.
   - Extract the relevant list (`data['results']`).
   - Pass to `pd.DataFrame()` and filter columns.
5. **Scale to all pages via a loop:**
   - Create an empty DataFrame.
   - Loop from page 1 through the total number of pages.
   - On each iteration, fetch the page data, create a temporary DataFrame, and append it using `ignore_index=True`.
6. **Verify and export:** Check `.shape` and use `.to_csv()`.
7. **(Optional) Publish the dataset:** Upload to Kaggle.

## 7. Examples
- **IRCTC / MakeMyTrip analogy:** Different companies sharing data securely via API.
- **Facebook multi-platform analogy:** A single database powering web, Android, and iOS via API.
- **TMDB Top Rated Movies dataset:** The main worked example, extracting 8,551 movies across 428 pages into a 7-column DataFrame.

## 8. Best Practices and Tips
- Always obtain and use your own API key rather than sharing keys, due to rate limits.
- Use a JSON Viewer tool to visually inspect unfamiliar JSON structures before coding.
- Always use `ignore_index=True` when looping through and appending API results to a combined DataFrame.
- Plan out your target DataFrame's columns in advance.
- Practice this workflow with different APIs (e.g., via RapidAPI) to reinforce learning.

## 9. Key Takeaways
- APIs allow separate software systems to communicate securely.
- API responses (JSON) map naturally onto Pandas DataFrames.
- Extracting data from paginated APIs involves hitting URLs in a loop, reshaping the data, and appending it cleanly.
- The session produced a real dataset of 8,551 movies exported to `movies.csv`.
- Self-built datasets can be uploaded to Kaggle to boost credibility and open up career opportunities.
