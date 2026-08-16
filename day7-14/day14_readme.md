# 1. Title
**Framing the Problem: A Data Scientist's Approach (Netflix Churn Case Study)**

## 2. Overview
This session (Day 14) marks the beginning of a deeper, step-by-step breakdown of the ML DLC stages introduced earlier, starting with the very first step: **Framing the Problem**. 

Using a detailed hypothetical case study of working as a Lead Data Scientist at Netflix tasked with increasing revenue, the speaker walks through how a vague business problem is progressively converted into a well-defined machine learning problem. The session covers converting a business problem into a mathematical problem, identifying the problem type, checking for existing solutions, determining data requirements, defining success metrics, deciding between online and batch learning, and checking underlying assumptions — framed as a general thought process for problem-solving as a data scientist rather than a rigid checklist.

## 3. Detailed Notes

### 3.1 Why This Topic Matters
- The previous session (Day 13) covered an end-to-end project on a very simple dataset; from this session onward, each step of that overall process will be broken down and studied individually, starting with Framing the Problem.
- As a junior data scientist joining a company, one typically works on a small, specific task (e.g., processing data). As one grows into leadership positions, the responsibility shifts to planning at a high level how a business problem will be solved.
- **The core question addressed in this session:** given a business problem, how can it be converted into a machine learning problem, and then solved?

### 3.2 Case Study Setup: Netflix
- **Scenario:** Assume you are a Lead Data Scientist at Netflix.
- A high-level meeting takes place discussing how to increase Netflix's revenue. As Head of the Data Science team, you're asked for your thoughts.

### 3.3 Step 1: Convert the Business Problem into a Mathematical Problem
**Identifying the Approach**
Three broad ways to increase revenue are considered:
1. Bring in more new customers via better marketing.
2. Charge existing customers more.
3. Reduce the number of existing customers leaving the platform (reduce churn).

Reasoning: bringing new customers is difficult, and charging existing customers more is considered a poor approach, so the chosen direction is: **reduce the churn rate of existing customers**.

**Understanding Churn Rate**
- Churn rate is described as the percentage of a platform's active users who leave the platform in a given period (e.g., monthly).
- Hypothetical numbers used: assume Netflix's current churn rate is 4%, and the target is to bring it down to 3.75% or 3.5%.

**Resulting Problem Statement**
- The business problem ("increase revenue") is converted into a mathematical problem: **reduce the churn rate from 4% to 3.75%**.
- This gives a clear, actionable goal to communicate to the team.

### 3.4 Step 2: Identify the Type of Problem and "See the Big Picture"
**Determining the Actual Task**
- Identify what type of problem is being solved — supervised or unsupervised, regression or classification.
- **Clarification:** the task is not to predict the overall churn rate, but to identify *which* customers are about to leave ("yes or no" for each customer) so they can be retained.

**Deciding on the End Product / Action**
- Immediate action chosen: identify at-risk customers and offer them a discount on their next month's subscription.

**Refining from Classification to Regression**
- **Initial framing:** supervised classification problem (predicting whether they will leave: yes/no).
- **Revised approach:** generate a score between 0 and 100 for each customer representing the probability that they will leave. Customers with a higher leave-probability get a bigger discount. 
- **Conclusion:** this reframes the problem from classification to a regression problem.

### 3.5 Step 3: Check for Existing/Current Solutions
- Before building something from scratch, check whether a current solution already exists.
- Example finding: an existing model already predicts Netflix's overall churn rate. Even though this addresses a different problem, it can still provide useful inspiration (e.g., learning what factors the existing team considered).

### 3.6 Step 4: Determine Data Requirements
Guiding question: to determine the probability that a customer will leave, what factors/data would be relevant?
- **Watch time:** how many hours spent, split between browsing and watching.
- **Search behavior:** searches that didn't return what the customer wanted.
- **Content abandonment:** starting content but stopping partway through.
- **Recommendation engagement:** how many recommendations are clicked.

**Collaboration required:** this requires working with a Data Engineer to build a data warehouse containing all needed columns extracted from the raw production database.

### 3.7 Step 5: Define Metrics to Measure Success
Decide how to determine whether the model is successful.
- **Approach 1:** compare predicted churn rate against actual churn rate.
- **Approach 2:** check whether the *specific* customers you predicted would leave are the ones who actually leave.
- Metrics act as a "North Star" guiding the team.

### 3.8 Step 6: Decide Between Online Learning and Batch Learning
- **Batch learning:** train the model, deploy it, and periodically retrain offline with new data.
- **Online learning:** the model continuously learns from incoming data in near real-time.
- **Reasoning:** watch-time behavior on Netflix is highly volatile. Online learning would be preferred, but practical difficulties might necessitate batch learning. This must be factored in early.

### 3.9 Step 7: Check Assumptions
- **Assumption 1 (Feature availability):** verify with the data engineer that the requested features actually exist.
- **Assumption 2 (Geographic generalization):** check if a single global model is valid, or if geography-based model variations are needed (e.g., US vs. India).

### 3.10 Closing Remarks: Why This Thought Process Matters
- There's no single fixed, "textbook" procedure — the video illustrates the thinking process itself.
- **Key message:** to be a good data scientist, one must think deeply about the problem before starting to code.
- Leadership positions go to those who demonstrate this kind of problem-solving thought process early on.

## 4. Key Concepts
- **Framing the Problem** is the foundational step of the ML DLC.
- The overall thought process includes: (1) business to math problem, (2) identifying problem type, (3) checking existing solutions, (4) determining data needs, (5) defining success metrics, (6) deciding on learning type, and (7) checking assumptions.
- Initial problem framings can evolve (e.g., moving from classification to regression).
- Leadership/career progression in data science is tied to structured problem-solving, not just coding.

## 5. Important Definitions
- **Churn Rate:** The percentage of a platform's active users who leave within a given period.
- **Framing the Problem:** Converting a business problem into a clearly defined, solvable problem statement.
- **Big Picture:** Understanding what the end product will actually be and do.
- **North Star (metrics):** A guiding reference metric that helps confirm whether the work is correct and on track.
- **Online Learning:** A learning approach where the model continuously learns from incoming data in real time.
- **Batch Learning:** A learning approach where the model is periodically retrained offline using newly extracted data.
- **Data Warehouse:** A structured data store built by a data engineer from a company's backend database.

## 6. Algorithms / Workflows

### General Problem-Framing Thought Process
1. Convert the business problem into a mathematical problem.
2. Identify the exact type of problem and see the big picture (supervised/unsupervised, classification/regression, actual end product).
3. Refine the problem type based on deeper reasoning.
4. Check for existing/current solutions for inspiration.
5. Determine what data is needed and collaborate with Data Engineers.
6. Define metrics to measure success.
7. Decide between online learning and batch learning based on data volatility and pipeline practicality.
8. Check and verify assumptions (feature availability, generalizability).

## 7. Examples
- **Target Churn Rate Example:** Reducing churn rate from 4% to 3.75%.
- **Discount-Based Retention Example:** Evolving from a flat 50% discount to a variable discount based on predicted probability.
- **Search & Watch-Time Examples:** Failed searches (e.g., searching for "Matrix" and not finding it) or browsing without streaming as churn-risk indicators.
- **Existing Solution Example:** An existing overall churn prediction model used as a source of inspiration.
- **Volatility Example:** Lockdown periods or holidays causing shifts in behavior, justifying online learning.
- **Geographic Assumption Example:** Questioning whether a single model works equally well for US and Indian users.

## 8. Best Practices and Tips
- Always attempt to convert a vague business problem into a clear, quantifiable mathematical problem before proceeding.
- Clearly distinguish between related but distinct problems (e.g., predicting aggregate churn rate vs. identifying individual at-risk customers).
- Reconsider and refine your problem type (e.g., toward regression) based on practical considerations like cost.
- Invest significant time in thinking through data needs before rushing into data collection.
- Define clear success metrics early.
- Explicitly check and verify your assumptions before committing significant resources.
- Think deeply about a problem before starting to code — course correction after starting in a wrong direction is very expensive.

## 9. Key Takeaways
- Framing the Problem requires a data scientist to convert a vague business problem into a well-defined, quantifiable ML problem.
- Initial problem framings can and should evolve through deeper reasoning.
- Success metrics act as a guiding "North Star."
- The choice between online and batch learning should be driven by the volatility of the data and pipeline considerations.
- Checking assumptions (data availability, generalizability) is an essential step before committing to a technical approach.
- Deep, structured thinking before coding is a key differentiator between a "coder" and an effective, leadership-capable data scientist.
