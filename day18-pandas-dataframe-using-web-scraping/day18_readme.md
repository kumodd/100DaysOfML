# 1. Title
**Data Gathering Part 4: Web Scraping (AmbitionBox Company Data)**

## 2. Overview
This session, recorded by the speaker while traveling on a flight, is the fourth and final video in the Data Gathering series, covering web scraping. 

Using the company review site AmbitionBox (similar to Glassdoor) as the target, the speaker demonstrates scraping company data (name, rating, review count, company type, headquarters, age, employee count, tags, and description) across multiple pages using `requests` and `BeautifulSoup`. It includes handling a 403 "access denied" error via request headers, inspecting HTML structure via browser DevTools, extracting data using tags and CSS classes, and finally looping across pages to build a combined Pandas DataFrame.

## 3. Detailed Notes

### 3.1 Context and Setup
- **Target website:** AmbitionBox (company review/interview-details platform).
- **Goal:** extract full company data from AmbitionBox's company listing pages.
- **Key difference from APIs:** this website does not provide an API. When no direct data access exists, web scraping is the only option.
- **Pagination discovery:** changing the page number in the URL (e.g., `?page=2`) navigates to different pages. The speaker found approximately 333 pages total.
- **Planned workflow:** iterate sequentially through pages, extracting 9 columns: Name, Rating, Reviews, Company Type, Headquarters, Age, Employees, Tags, and Description.

### 3.2 Step 1: Setup and Initial Request
**Import required libraries:**
```python
import pandas as pd
import requests
from bs4 import BeautifulSoup
```
- `BeautifulSoup` (bs4) is the main library used for web scraping.

**First request attempt (fails with 403):**
```python
response = requests.get(url)
```
- A status code of 403 is returned, meaning access denied. This is because sites maintain a `robots.txt` file blocking automated scripts.

**Fix — sending browser-like headers:**
Make the request appear as if it's coming from a real browser by sending a User-Agent header:
```python
headers = {'User-Agent': '<browser user-agent string>'}
response = requests.get(url, headers=headers)
```
- This request succeeds, returning the full raw HTML.

### 3.3 Step 2: Parsing HTML with BeautifulSoup
**Creating the BeautifulSoup object:**
```python
soup = BeautifulSoup(response.text, 'lxml')
```
- `lxml` is the HTML parser built into bs4.
- `soup.prettify()` can be used to view formatted HTML.

**Using browser DevTools:**
- Right-click on the live webpage and choose "Inspect".
- Hovering over elements reveals their nested HTML structure.
- **Key observation:** the container structure repeats identically for every company listed, forming the basis for looping.

### 3.4 Step 3: Extracting Individual Fields (Initial Exploration)
**Extracting h2 tags (company names):**
```python
soup.find_all('h2')
```
- Returns 30 items. `.text.strip()` cleans whitespace.

**Extracting ratings:**
```python
soup.find_all('p', class_='rating')
```
- Filtered by class because `<p>` tags are used extensively elsewhere.

**Extracting review counts:**
```python
soup.find_all('a', class_='review-count')
```

### 3.5 Step 4: The Better Approach — Extract Per-Company Containers First
**Key strategic insight:** rather than searching the whole page for all instances of a tag (which mixes data together), extract the container div for each individual company, then search within that container.

**Extracting all company containers:**
```python
company = soup.find_all('div', class_='company-content-wrapper')
```
- Looping `for i in company:` solves ambiguity problems.

### 3.6 Step 5: Extracting Each Field Within the Per-Company Loop
Within a single company's container, there is exactly one `h2` and one `rating`, so `.find()` (single match) is used instead of `.find_all()` (list match).
```python
name = []
rating = []
reviews = []

for i in company:
    name.append(i.find('h2').text.strip())
    rating.append(i.find('p', class_='rating').text)
    reviews.append(i.find('a', class_='review-count').text.strip())
```

### 3.7 Step 6: Extracting the Ambiguous Fields (Company Type, HQ, Age, Employees)
Within a single company div, searching for `<p class="infoEntity">` returns a list containing multiple items. They must be differentiated by list position:
```python
ctype, hq, how_old, employees = [], [], [], []

for i in company:
    info = i.find_all('p', class_='infoEntity')
    ctype.append(info[0].text)
    hq.append(info[1].text)
    how_old.append(info[2].text)
    employees.append(info[3].text)
```

### 3.8 Step 7: Description Field
Inside a `<p>` tag with class `description`. Extracted similarly but skipped in the live demo for time.

### 3.9 Step 8: Assembling the DataFrame (Single Page)
```python
df = pd.DataFrame({
    'Name': name,
    'Rating': rating,
    'Reviews': reviews,
    'Company_Type': ctype,
    'Head_Quarter': hq,
    'How_Old': how_old,
    'Employees': employees
})
```
- Creates exactly 30 rows (one page).

### 3.10 Step 9: Scaling Up — Looping Across Multiple Pages
```python
final = pd.DataFrame()

for j in range(1, 11):
    url = '<AmbitionBox company listing URL with page number>'.format(j)
    response = requests.get(url, headers=headers)
    soup = BeautifulSoup(response.text, 'lxml')
    
    # ... all per-page extraction logic ...
    
    df = pd.DataFrame({...})
    final = final.append(df, ignore_index=True)
```
- `j` replaces the page number.
- `ignore_index=True` ensures continuous index numbers across the merged dataset.
- Verified on 10 pages yielding 300 rows.

## 4. Key Concepts
- Web scraping is a last-resort gathering method when no API exists.
- Browser-like User-Agent headers are required to bypass basic bot blockers.
- `BeautifulSoup` enables HTML searching by tag and CSS class.
- A critical strategy: extract individual item containers first, then search within each container to prevent cross-contamination.
- `ignore_index=True` is needed for clean pagination.

## 5. Important Definitions
- **Web Scraping:** Programmatically extracting data from raw HTML.
- **robots.txt:** Server file dictating automated access rules.
- **403 (HTTP Status Code):** Server refused to authorize the request (bot blocked).
- **User-Agent header:** Identifies the client software making the request.
- **BeautifulSoup (bs4):** Python HTML parsing library.
- **.find_all():** Returns all matching elements as a list.
- **.find():** Returns the single first matching element.
- **Container Div:** HTML element holding all data for one logical item.

## 6. Algorithms / Workflows

### Workflow: Scraping a Single Page
1. **Make request with headers:** `requests.get(url, headers=headers)`
2. **Parse HTML:** `soup = BeautifulSoup(response.text, 'lxml')`
3. **Inspect target page:** use browser DevTools to find tags and classes.
4. **Extract repeating item containers:** `soup.find_all('div', class_='...')`
5. **Loop through containers:** use `.find()` for single tags and `.find_all()[index]` for multiple identical tags.
6. **Assemble list data into a DataFrame.**

### Workflow: Scaling to Multiple Pages
1. Create empty `final` DataFrame.
2. Loop over desired page range.
3. Build URL dynamically using `.format(j)`.
4. Fetch page, parse, run single-page extraction, create temp `df`.
5. Append `df` to `final` using `ignore_index=True`.
6. Verify shape.

## 7. Examples
- **AmbitionBox:** Main example extracting TCS, Accenture, etc.
- **h2 tags:** Extracted company names, requiring `.strip()` to fix whitespace.
- **<p> tag ambiguity:** The `infoEntity` class contained 4 different fields in a list per company (Type, HQ, Age, Employees), necessitating positional list extraction.

## 8. Best Practices and Tips
- If an HTTP request fails with a 403, pass a User-Agent header instead of giving up.
- Rely heavily on browser DevTools ("Inspect Element") before coding.
- Always filter common tags (like `<p>` or `<a>`) by their `class_` attribute.
- Extract individual item containers first, rather than querying the entire page at once.
- Use `.find()` when only one match exists per container to avoid list indexing syntax.
- Test scraper logic on a tiny subset of pages (like 1-10) before running a full 300+ page loop.
- Use `ignore_index=True` to append dataframes cleanly.

## 9. Key Takeaways
- This session concludes the Data Gathering mini-series.
- Web scraping uses `requests` and `BeautifulSoup` to parse structure from raw HTML.
- Extracting containers first resolves the ambiguity of repeating classes.
- Distinguishing between `.find()` and `.find_all()` is a core practical skill.
- Paginated web scraping follows the exact same looping/appending pattern as paginated API extraction.
