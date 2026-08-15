# Batch Learning (Offline Learning) vs. Online Learning in Machine Learning

## Overview
This lecture explains the two major approaches to training Machine Learning models:
- Batch Learning (Offline Learning)
- Online Learning

The discussion begins with Batch Learning, the traditional approach in which a model is trained using the complete dataset before deployment. It then examines the limitations of this approach, including model stagnation, scalability issues, hardware constraints, and delayed adaptation to changing data.

The lecture introduces Online Learning as an alternative that updates models incrementally as new data arrives. It discusses situations where Online Learning is beneficial, introduces Out-of-Core Learning for handling datasets larger than memory, provides practical applications, mentions implementation libraries, and concludes with the challenges and risks associated with Online Learning.

*Note: The provided transcript is a summarized version of the lecture rather than a verbatim transcription. The notes below include only the information explicitly present in the transcript.*

## Detailed Notes

### Introduction
Machine Learning models can be trained using two fundamental approaches:
1. Batch Learning (Offline Learning)
2. Online Learning

The key distinction between them lies in:
- How the model is trained.
- How new data is incorporated after deployment in a production environment.

### Batch Learning (Offline Learning)
**Definition**
Batch Learning is the conventional approach to Machine Learning training.

**Characteristics:**
- The entire dataset is used during training.
- Training occurs all at once.
- There is no incremental learning after deployment.

**Workflow**
The lecture describes the following workflow:
1. Collect the complete dataset.
2. Train the model on a local machine (offline).
3. Test and validate the model.
4. Deploy the trained model to the production server.

The deployed model remains unchanged until it is retrained.

**Workflow Diagram**
```text
Collect Dataset
        ↓
Train Offline
        ↓
Test Model
        ↓
Deploy to Server
        ↓
Serve Predictions
```

**Model Stagnation**
Once deployed:
- The model becomes static.
- It cannot automatically learn from newly arriving data.
- Changes in the business environment are not reflected until retraining occurs.
- As data evolves, a model trained on older data may become outdated.

**Example: Movie Recommendation System**
The lecture uses a movie recommendation system (e.g., a platform like Netflix) to illustrate this limitation.
- **Scenario**:
  - The recommendation model initially performs well.
  - New movies are released regularly.
  - The existing model has no knowledge of these additions.
- To remain effective, developers must periodically:
  1. Merge newly collected data with existing data.
  2. Retrain the model.
  3. Test the updated model.
  4. Redeploy the model.
- This retraining cycle repeats continuously.

### Limitations of Batch Learning
**1. Data Scalability**
As datasets grow rapidly:
- Training on the complete dataset becomes increasingly expensive.
- Processing time increases.
- Infrastructure requirements become larger.
- Large-scale applications (such as social networks) may generate datasets that become impractical to process as a single batch.

**2. Hardware and Connectivity Constraints**
Some deployment environments do not have reliable internet connectivity.
- **Examples mentioned:**
  - Applications used by soldiers in remote areas.
  - Software deployed inside satellites.
- In such cases:
  - Retrieving the deployed model for retraining is difficult or impossible.
  - Updating the model becomes a significant challenge.

**3. Delayed Response (Latency)**
Batch Learning is not suitable when rapid adaptation is required.
- **Example**: The lecture presents a scenario involving a major, time-sensitive event (e.g., the Indian government's demonetization).
- If the recommendation model is updated only once every 24 hours:
  - It cannot immediately recognize users' increased interest in the new event.
  - Users continue receiving outdated or irrelevant recommendations until the next retraining cycle.

**Need for an Alternative**
The limitations of Batch Learning motivate the use of Online Learning, where models can update continuously as new information becomes available.

### Online Learning
**Definition**
Online Learning is a Machine Learning approach in which the model learns incrementally.

Instead of training once on a fixed dataset:
- New data continuously arrives.
- The deployed model is updated incrementally.
- The model adapts to changing patterns over time.

**Workflow**
1. Deploy an initial model.
2. Receive new incoming data.
3. Update the model incrementally.
4. Continue making predictions using the updated model.
5. Repeat as additional data arrives.

**Workflow Diagram**
```text
Initial Model
      ↓
Receive New Data
      ↓
Update Model
      ↓
Serve Predictions
      ↓
Repeat Continuously
```

### When to Use Online Learning
Online Learning is particularly useful when data distributions change over time.

**Concept Drift**
The lecture identifies concept drift as a major reason for using Online Learning.
Concept drift refers to situations where:
- The underlying patterns in the data evolve over time.
- A model must continually adapt to remain accurate.
- **Examples mentioned:**
  - Stock market prediction.
  - E-commerce customer behavior.

### Out-of-Core Learning
**Definition**
Out-of-Core Learning enables training on datasets that are too large to fit into memory.
Instead of loading the complete dataset:
1. Divide the data into smaller batches.
2. Process one batch at a time.
3. Incrementally update the model.

This allows effective training despite memory limitations.

### Applications of Online Learning
The lecture discusses several practical applications:

- **Chatbots**
  - **Examples:** Alexa, Google Assistant
  - These systems continuously adapt to user interactions.

- **Predictive Keyboards**
  - **Example:** SwiftKey
  - The keyboard improves its text prediction capabilities based on user typing behavior.

- **Recommendation Systems**
  - **Example:** YouTube
  - Recommendations change dynamically according to a user's latest interactions.

### Tools Mentioned
The lecture highlights two libraries for implementing Online Learning workflows:
- River
- Vowpal Wabbit

### Challenges and Risks
Although Online Learning offers significant advantages, it introduces additional complexity.

**Risk of Poor Incoming Data**
If incoming data is corrupted, noisy, or biased, the model may learn incorrect patterns.

**Monitoring Requirements**
Online Learning requires:
- Continuous monitoring of model performance.
- Mechanisms to detect problems.
- The ability to revert the model to a previous stable version if necessary.

### Batch Learning vs. Online Learning

| Aspect | Batch Learning (Offline Learning) | Online Learning |
| :--- | :--- | :--- |
| **Training** | Entire dataset at once | Incremental updates |
| **Learning After Deployment** | No | Yes |
| **Model Updates** | Periodic retraining | Continuous updates |
| **Adaptation to New Data** | Delayed | Real-time |
| **Scalability** | Limited for very large datasets | Better suited for data streams |
| **Concept Drift** | Poor handling | Designed to adapt |
| **Memory Usage** | Requires complete dataset during training | Supports incremental processing |
| **Infrastructure** | Offline training followed by deployment | Continuous server-side updates |
| **Complexity** | Simpler | More complex |
| **Risk** | Model becomes outdated | Risk of learning from corrupted or biased data |

## Key Concepts
- Batch Learning
- Offline Learning
- Online Learning
- Incremental Learning
- Model Deployment
- Model Retraining
- Production Environment
- Data Scalability
- Concept Drift
- Latency
- Out-of-Core Learning
- Continuous Model Updating
- Recommendation Systems
- Chatbots
- Predictive Keyboards
- River
- Vowpal Wabbit

## Important Definitions
- **Batch Learning (Offline Learning)**: A Machine Learning approach where the entire dataset is used to train a model before deployment, with no incremental learning afterward.
- **Online Learning**: A Machine Learning approach in which a deployed model is updated incrementally as new data becomes available.
- **Incremental Learning**: A learning process in which a model continuously incorporates new information instead of being retrained from scratch.
- **Concept Drift**: A situation in which the underlying patterns or relationships in the data change over time, requiring the model to adapt.
- **Out-of-Core Learning**: A training technique for datasets that do not fit into memory by processing the data in smaller batches.

## Algorithms / Workflows

### A. Batch Learning Workflow
1. Collect the complete dataset.
2. Train the model offline.
3. Test and validate the model.
4. Deploy the model.
5. Collect new data.
6. Merge old and new datasets.
7. Retrain the model.
8. Test again.
9. Redeploy.

### B. Online Learning Workflow
1. Deploy an initial model.
2. Receive new incoming data.
3. Update the model incrementally.
4. Continue serving predictions.
5. Repeat the update process as new data arrives.

### C. Out-of-Core Learning Workflow
1. Split a large dataset into smaller batches.
2. Load one batch into memory.
3. Train or update the model.
4. Load the next batch.
5. Continue until all batches are processed.

## Examples
- **Example 1: Movie Recommendation System**
  - A recommendation model initially performs well.
  - New movies are added regularly.
  - The model must be retrained periodically to include the new data.

- **Example 2: Time-Sensitive Events**
  - A major event (e.g., the Indian government's demonetization) causes a sudden shift in user interests.
  - A Batch Learning model updated only once every 24 hours cannot immediately reflect this change.
  - Users continue receiving outdated recommendations until the next retraining cycle.

- **Example 3: Chatbots**
  - Services such as Alexa and Google Assistant adapt their behavior through Online Learning based on user interactions.

- **Example 4: Predictive Keyboard**
  - SwiftKey improves text prediction as users continue typing.

- **Example 5: Recommendation System**
  - YouTube dynamically adjusts recommendations according to users' latest interactions.

## Best Practices and Tips
- Use **Batch Learning** when:
  - The dataset is relatively stable.
  - Periodic retraining is sufficient.
  - Real-time adaptation is not required.
- Use **Online Learning** when:
  - Data arrives continuously.
  - Patterns change over time (concept drift).
  - Real-time model adaptation is important.
- Apply **Out-of-Core Learning** for datasets that exceed available memory.
- Continuously monitor Online Learning systems to detect corrupted, noisy, or biased incoming data.
- Maintain mechanisms to roll back to a previous model version if online updates negatively affect performance.

## Key Takeaways
- Batch Learning trains models once using the complete dataset and requires periodic retraining to incorporate new information.
- The traditional Batch Learning workflow consists of offline training, testing, deployment, and periodic retraining as new data becomes available.
- Major limitations of Batch Learning include poor scalability, deployment constraints in disconnected environments, and delayed adaptation to rapidly changing data.
- Online Learning addresses these limitations by updating models incrementally as new data arrives.
- Online Learning is particularly suitable for environments experiencing concept drift, where data patterns evolve over time.
- Out-of-Core Learning enables incremental training on datasets larger than available memory by processing data in small batches.
- Practical applications discussed include chatbots, predictive keyboards, and recommendation systems.
- While Online Learning provides greater adaptability, it also introduces risks related to poor-quality incoming data and requires continuous monitoring and rollback mechanisms.
