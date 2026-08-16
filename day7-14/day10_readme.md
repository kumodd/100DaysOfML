# 1. Title
**Job Roles in Data Science & Machine Learning: Data Engineer, Data Analyst, Data Scientist, and ML Engineer**

## 2. Overview
This session covers the various job profiles available in the field of data science and machine learning, addressing the common confusion job-seekers face when they encounter multiple similar-sounding titles. The speaker explains that these four job roles — Data Engineer, Data Analyst, Data Scientist, and ML Engineer — each map to a different stage of the ML Development Life Cycle (ML DLC) discussed in the previous session. 

For each role, the speaker covers the core responsibilities, the required skills, and gives guidance on which role a person might want to pursue. The session closes with a side-by-side comparison of the four roles across several skill dimensions.

## 3. Detailed Notes

### 3.1 Introduction: Why This Topic Matters
The speaker states that job searching in the data science/ML field can be confusing because there are many different job profiles.
- The video's purpose is to make sure viewers know that studying ML is not enough — they also need to know that different job profiles exist in this space.
- The speaker mentions sharing a screen recording of a job-search-engine website (unnamed) with many startup/company jobs posted, and encourages viewers to explore it after watching.
- **Demonstration on a job search engine:** Searching "Machine Learning Engineer" shows job listings along with salary information; the speaker cites an example figure of 7-27 lakhs salary range for a Machine Learning Engineer role, and notes some companies are actively hiring for this role.
- Searching further reveals other related profiles: Data Scientist (a different job profile from ML Engineer, though related), Data Analyst, and Data Engineer.
- The speaker recounts personally getting confused when job-searching about which of these profiles to pursue, which motivated making this video.
- The speaker promises to cover, for each job profile: what responsibilities it involves, what skills are needed, and roughly what salary to expect. A "roadmap" is also mentioned as a resource with more detail on the overall process.

### 3.2 Connection to the ML Development Life Cycle (Day 1 recap)
Speaker explicitly revisits/references the prior day's content: the ML Development Life Cycle video, without re-explaining it in full — recapped briefly below as the speaker did.
- The speaker recaps that the previous video's steps were, in order: Plan → bring in data → process the data → (EDA/update) → modeling (training algorithms) → evaluate → deploy → optimize.
- **The key point made:** one person typically cannot do all of this alone, especially at a large company — the overall ML DLC process is too large for a single person to own.
- Because of this, different job roles were defined for different stages of this process, and the four roles discussed in this session — Data Engineer, Data Analyst/Data Scientist, ML Engineer — each own a piece of this overall process.

### 3.3 Role 1: Data Engineer
**Core job:** Bringing data and making it available in a proper table/format so that downstream teams can use it.
In student/practice projects, data is often just a single readily-available file; in large companies, this is not the case.

**OLTP vs. Data Warehouse:**
- **OLTP = Online Transaction Processing.** Example given: a website like Flipkart has a live production database (OLTP database) used to run its app/website in real time.
- Data science/analytics teams should not directly work on this live/running database, since it's actively serving users.
- Instead, a separate structure needs to be built from the OLTP database — this is called OLAP (Online Analytical Processing).
- The Data Engineer's job is to create this OLAP-style structure from the website's live database, so that the data science/analytics teams can work on it without disturbing the live/production database. This can also simply be called a database → data warehouse transformation.
- **Most important task:** Building a data warehouse from a database. This is described as difficult, specialized work requiring strong software skills and database knowledge.

**Other responsibilities:**
- Bringing in data from multiple sources — e.g., a company's own database, a second source, and web-scraped data from a third-party website — and delivering it in the correct/unified format to the analytics team.
- Managing/storing data in services/warehouses as discussed above.
- Building data pipelines and APIs to make data access easier — once a data warehouse is built, pipelines are set up so that any team needing text/data access can get it easily.
- Periodic maintenance of databases and data warehouses — handling issues, monitoring pipelines to ensure everything runs correctly on schedule.

**Industry importance:** This role is described as very important, especially in large organizations with large amounts of data. The speaker states that data engineers are currently underrated/undervalued relative to their importance ("data is gold," and handling it properly is very important).
**Salary note:** Data Engineers receive very good salaries, partly attributed to relatively few people having strong-enough skills in this area, keeping supply low.

**Skills required to become a Data Engineer:**
- Strong software engineering skills — described almost like a backend developer, with knowledge of databases and servers.
- Knowledge of data structures and algorithms.
- Knowledge of programming languages — Python, Java, or Scala are given as examples.
- Knowledge of different types of databases — both SQL and NoSQL.
- Knowledge of Big Data tools — examples given: Apache Spark, Hadoop, Hive.
- Good experience with cloud platforms — AWS, GCP are mentioned as examples.
- Should be comfortable with distributed systems and have good system design knowledge.
- Should know how to build data pipelines using orchestration tools — Apache Airflow is given as an example of a popular tool.

*The speaker personally notes this is the area of the entire process that they find hardest/most intimidating, describing it as "hardcore software" work.*

### 3.4 Role 2: Data Analyst
**One-line description:** A person whose core job is to run analysis on data and communicate/report findings to people (leadership).

Recap of ML DLC connection: once a Data Engineer gathers data, the next step is for someone to clean/screen that data and produce reports/insights from it — this is the Data Analyst's job.
**Core idea:** The Data Analyst understands what's happening in the available data and tells its "story" — e.g., explaining why a particular product performed a certain way, or why last year's profit declined, by finding answers from within the data.

**Responsibilities:**
- Cleaning and organizing data — data rarely arrives in the right/clean format, so cleaning it is typically the first task.
- Channelizing/extracting insights from data — pulling out the underlying "small story" hidden in the data; creating data visualizations is called out as a very important part of this.
- Reporting to senior management — since leadership typically doesn't want to look at raw numbers/tables directly, the analyst must use graphs and similar visuals to tell the data's "story" effectively.
- **Related job title:** Business Analyst is a similar role. Both jobs involve extracting data and communicating it, but Data Analyst leans more toward engineering/data-heavy skills, while Business Analyst leans more toward management/business-focused skills.
- Produces and maintains reports and slides, presenting them in meetings.

**Skills required to become a Data Analyst:**
- Strong knowledge of statistics — needed to extract the "story" from data.
- Knowledge of a programming language — Python or R are given as examples; described as very important.
- Strong logical/analytical thinking ("common sense") — needed to interpret data intuitively.
- Domain/business knowledge relevant to the industry.
- Strong communication skills — needed since the analyst interacts with many people and presents findings to other teams.
- Good understanding of data mining.
- Good data visualization skills — described as important for data storytelling.
- Data storytelling — described as somewhat of an art.
- SQL knowledge, for working with databases.

### 3.5 Role 3: Data Scientist
**One-line description:** A Data Scientist is described as a mix of a software engineer, a statistician, and someone with strong overall skills.

The Data Scientist is described as someone who can be a "jack of all trades" across the ML DLC — able to potentially do the work of a Data Engineer or Data Analyst if needed.

**Key distinction between Data Analyst and Data Scientist:**
- A Data Analyst looks toward the past — what happened, why it happened, how it happened, reviewing historical outcomes.
- A Data Scientist looks toward the future — building things based on understanding the data to solve forward-looking problems.

**Examples given for Data Scientist work:**
- Building a way to increase sales.
- Building a recommendation engine to give customers a better experience.
- Building a route optimizer to get something to a destination as quickly/efficiently as possible.

Because the Data Scientist role can span the "full" ML DLC, they should ideally know a bit of everything covered in that lifecycle.
*Real-world scope note: In a large company, a Data Engineer will bring the data, provide a report, and the Data Scientist reads that report, creates the model (best-performing model), while some other role integrates the model into a website/app.*

**Skills required to become a Data Scientist:**
- Broad knowledge across roles — essentially all the skills mentioned for other roles.
- Should have decent knowledge of software engineering basics.
- Communication skills should be strong, since the Data Scientist needs to talk to different people.

### 3.6 Role 4: ML Engineer (Machine Learning Engineer)
The speaker notes there's often confusion where people assume "if it's about machine learning, it must be the ML Engineer" — but this is actually a fairly narrow, specific role.

**Why this role exists:** Typically, a Data Scientist doesn't know software development well, and software developers don't know data science well. So there's a gap — someone bridging both is needed to take a completed model and integrate it into a website or mobile app. This bridging role is the ML Engineer.

**Responsibilities:**
- Deploying an already-built ML model into production — described as the most important task ("model to production").
- Optimizing the model/scripts for production — e.g., optimizing how efficiently requests are handled, how training/data flows occur, and taking backups of the model during training.
- Monitoring and maintenance of the deployed model — watching over it, and handling tasks like replacing/updating models as needed.

**Skills required to become an ML Engineer:**
- Strong programming language knowledge.
- Comfortable with distributed systems.
- Backend/production deployment knowledge — how to properly put things into production.
- Knowledge of how to retrain/replace models correctly.
- Some knowledge of machine learning concepts in general.
- Strong software engineering skills.
- Good understanding of system design.

### 3.7 Comparison of the Four Roles
Speaker explicitly frames this as a comparison across the four roles on specific skill dimensions.

| Skill Dimension | Data Engineer | Data Analyst | Data Scientist | ML Engineer |
|---|---|---|---|---|
| **Business Acumen** | Not important | Medium to High | High | Medium |
| **Statistics / Domain Knowledge** | Not a core requirement | Should be good | Should be very strong | Not a strong requirement |
| **Data Storytelling** | Not needed | Very important | Important, but less central | Not needed |
| **Soft Skills / Communication** | Medium | Medium to High | Very High | Medium to High |
| **Programming Languages** | Should be very strong | Should know a language (Python/R) | Should know programming well | Should be very strong |
| **Distributed Systems Knowledge** | Should be strong | Not typically required | Not emphasized as a core requirement | Should be strong |

### 3.8 Closing Guidance
The speaker offers a simplified decision heuristic for viewers unsure which path to choose:
- If unsure, becoming a Data Scientist is recommended as a strong default (associated with higher pay).
- If someone doesn't want to work directly with large-scale distributed systems but instead just wants to "play with data," becoming a Data Analyst is suggested.
- If none of the above fit, consider becoming an ML Engineer.

**The speaker recommends two follow-up actions:**
- Check a blog link (mentioned in the video description) with more detail.
- Visit the referenced job-search website directly and research real job postings to see what companies are actually asking for in each role.

**General career advice:** Rather than asking seniors or teachers what skills are required for a role, directly check job websites to see what companies are demanding, and develop those specific skills.

## 4. Key Concepts
- Four core job profiles associated with the ML Development Life Cycle: Data Engineer, Data Analyst, Data Scientist, ML Engineer.
- Each role corresponds to a different stage/responsibility within the broader ML DLC process introduced in the previous session (Day 1).
- OLTP vs. OLAP distinction as the basis for why data engineering/data warehousing is needed.
- **Data Analyst vs. Data Scientist:** the key differentiator is looking at the past (Analyst) vs. building for the future (Scientist).
- ML Engineer exists specifically to bridge the gap between Data Scientists and software developers.
- Skill requirements and emphasis vary significantly across the four roles.

## 5. Important Definitions
- **OLTP (Online Transaction Processing):** A live, running production database that should not be directly used for analytics/data science work since it is actively serving users.
- **OLAP (Online Analytical Processing):** A separate data structure ("data warehouse") built from an OLTP database so that analytics teams can work on it without disturbing the live system.
- **Data Engineer:** The role responsible for bringing in data from various sources, transforming a live database into a data warehouse, building data pipelines/APIs, and maintaining these systems.
- **Data Analyst:** The role responsible for cleaning/organizing data and extracting insights to report to people, focused on understanding past events.
- **Business Analyst:** A role similar to Data Analyst but leaning more toward business/management skills rather than engineering-heavy data skills.
- **Data Scientist:** A broad role combining software engineering and statistics skills, capable of handling much or all of the ML DLC if needed, focused on building forward-looking solutions.
- **ML Engineer (Machine Learning Engineer):** The role responsible for taking an already-built ML model and deploying it into production, optimizing it, and monitoring/maintaining it.
- **Data Pipeline:** An automated system/process that fetches or moves data from one place to another so downstream teams can access it easily.

## 6. Algorithms / Workflows
**General Framing: Job Roles Mapped to ML DLC Stages**
- **Data Engineer** — sources and prepares raw data (via databases, warehouses, pipelines, APIs) so it's usable by downstream teams.
- **Data Analyst** — cleans, organizes, analyzes, and visualizes the data engineer's output to produce insights/reports (backward-looking).
- **Data Scientist** — uses processed data/insights to build predictive/forward-looking models and solutions; may cover multiple stages of ML DLC depending on company size.
- **ML Engineer** — takes a completed model from the Data Scientist and deploys, optimizes, monitors, and maintains it in production.

**Suggested Approach to Choosing a Role:**
- If undecided → default toward Data Scientist.
- If uninterested in large-scale distributed systems and just want to work with data directly → consider Data Analyst.
- If neither of the above fits → consider ML Engineer.

## 7. Examples
- **Flipkart OLTP example:** Flipkart's live website/app database is an OLTP database; the analytics team cannot work directly on it, so an OLAP data warehouse must be built instead.
- **Data Analyst storytelling example:** Explaining why a particular product's performance declined, or why profit dropped in the previous year, by analyzing historical data.
- **Data Scientist forward-looking examples:** Building a recommendation engine to improve customer experience, or building a route/delivery optimizer.
- **Cricket website data example:** Used to illustrate why domain knowledge matters for a Data Analyst.
- **Medical / banking domain example:** A Data Analyst working in a medical domain should understand medical treatment concepts, and one working in banking should understand banking systems.
- **Job-mobility example (Data Engineer):** A Data Engineer could move from working at Zomato to working at Flipkart without much friction, since the technical work is largely similar regardless of the business domain.

## 8. Best Practices and Tips
- To find out what skills a specific role actually requires, check real job postings on job-search websites directly rather than relying solely on advice from seniors or teachers.
- Data storytelling and visualization skills should be intentionally developed, since not everyone has a natural aptitude for it, and it's important for a Data Analyst.
- Understand the ML DLC stages as a framework for understanding how these four job roles relate to and depend on each other.

## 9. Key Takeaways
- The four major job roles in the data science/ML field — Data Engineer, Data Analyst, Data Scientist, and ML Engineer — correspond to different stages of the ML Development Life Cycle.
- Data Engineers focus on sourcing, structuring, and maintaining data, requiring strong software engineering and big-data skills.
- Data Analysts focus on cleaning data and extracting/communicating insights about the past, relying heavily on statistics, domain knowledge, and storytelling skills.
- Data Scientists are broader, forward-looking roles combining software engineering and statistics, capable of covering much of the ML DLC.
- ML Engineers specifically bridge the gap between data science and software engineering by deploying, optimizing, and maintaining models in production.
- Skill emphasis (business acumen, storytelling, communication, technical depth, distributed systems knowledge) differs meaningfully across these four roles.
- The speaker recommends researching actual job postings directly to understand real-world skill requirements for any of these roles.
