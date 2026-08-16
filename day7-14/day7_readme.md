# 1. Title
**Challenges in Machine Learning | Common Problems in Building and Deploying ML Systems**

## 2. Overview
This lecture discusses the major practical challenges encountered throughout the Machine Learning lifecycle, from collecting data to deploying and maintaining models in production.

Rather than focusing solely on algorithms, the lecture emphasizes that successful Machine Learning systems depend on high-quality data, proper feature engineering, robust deployment strategies, and operational management. It also introduces concepts such as sampling bias, overfitting, underfitting, software integration, deployment challenges, and MLOps.

> **Note:** The provided transcript is a summarized version of the lecture rather than a verbatim transcription. The notes below include only the information explicitly present in the transcript.

## 3. Detailed Notes

### 3.1 Introduction
Developing a Machine Learning model involves much more than selecting an algorithm. Real-world Machine Learning projects face challenges throughout the pipeline, including:
- Data collection
- Data quality
- Feature engineering
- Model training
- Model deployment
- Production maintenance
- Infrastructure and operational costs

### 3.2 Data Collection
**Challenge**
Obtaining data in real-world projects is significantly more difficult than working with ready-made datasets (e.g., CSV files used for learning or practice).

**Data Collection Methods Mentioned**
- API-based data collection
- Web scraping

**Practical Challenges**
Even these methods introduce additional complexity, making data acquisition one of the first major obstacles in an ML project.

### 3.3 Insufficient or Unlabeled Data
**Importance of Large Datasets**
The lecture references the paper: *"The Unreasonable Effectiveness of Data"*. Its central message, as presented in the lecture: Having a very large amount of data is often more valuable than choosing a particular algorithm.

**Data Labeling Challenge**
Many supervised learning tasks require manually labeled data.
*Example:* Image classification:
- Cat images
- Dog images

Each image must be manually assigned the correct label. The lecture highlights that this process is:
- Time-consuming
- Tedious
- Labor-intensive

### 3.4 Non-Representative Data
**Problem**
A Machine Learning model can only learn from the data it receives. If the training data does not accurately represent the real-world problem, the resulting model produces poor conclusions.

**Causes Mentioned**
1. **Sampling Noise**: Random variations in sampled data that reduce data quality.
2. **Sampling Bias**: The collected sample systematically fails to represent the actual population.

Both issues reduce model reliability.

### 3.5 Poor Quality Data
**Characteristics of Real-World Data**
The lecture notes that practical datasets often contain:
- Missing values
- Errors
- Noise

**Data Cleaning**
A significant portion of a data scientist's work involves:
- Cleaning data
- Preprocessing data

According to the lecture, approximately 60–80% of a data scientist's time may be spent on these activities.

### 3.6 Irrelevant Features
**Problem**
Including unnecessary features can reduce model performance. The lecture summarizes this using the principle: **Garbage In, Garbage Out (GIGO)**. Poor-quality or irrelevant inputs result in poor model outputs.

**Feature Engineering**
Feature engineering is important for:
- Selecting useful variables.
- Combining existing variables appropriately.

Proper feature engineering improves model performance.

### 3.7 Overfitting
**Definition**
Overfitting occurs when the model:
- Memorizes the training data.
- Fails to generalize to unseen data.

**Characteristics**
Instead of learning the overall trend, the model fits the individual training points too closely. As a result:
- Training performance may appear very good.
- Performance on new data becomes poor.

### 3.8 Underfitting
**Definition**
Underfitting is the opposite of overfitting. The model is:
- Too simple.
- Unable to capture the underlying patterns in the data.

**Characteristics**
Poor performance occurs even on the training dataset itself.

### 3.9 Software Integration
**Challenge**
A Machine Learning model alone is not sufficient. To become useful, it must be integrated into software applications such as:
- Websites
- Mobile applications
- Other software systems

**Compatibility Issues**
The lecture highlights challenges in making ML models compatible across:
- Different operating systems
- Web environments
- Programming languages (e.g., Java)

Integration therefore becomes an important engineering challenge.

### 3.10 Offline Learning and Deployment Challenges
**Offline Learning**
Offline learning requires:
- Taking the model offline.
- Retraining it using updated data.
- Redeploying the updated model.

This process is cumbersome and operationally expensive.

**Deployment**
Deploying Machine Learning models on cloud platforms such as AWS and Azure is described as an evolving area that may be less stable than traditional software deployment.

### 3.11 High Operational Costs
**Cost at Scale**
As the number of users increases, server infrastructure costs increase substantially. Running Machine Learning models for thousands of users can therefore become very expensive.

**MLOps**
To address operational challenges, the lecture introduces **Machine Learning Operations (MLOps)**. MLOps focuses on:
- Deployment
- Operations
- Monitoring
- Cost management

for Machine Learning systems.

### 3.12 Summary of Challenges
| Challenge | Description |
|---|---|
| **Data Collection** | Obtaining real-world data is difficult. |
| **Insufficient / Unlabeled Data** | Large labeled datasets are difficult to obtain. |
| **Non-Representative Data** | Poor sampling results in unreliable models. |
| **Poor Quality Data** | Missing values, errors, and noise require extensive preprocessing. |
| **Irrelevant Features** | Unnecessary variables reduce model quality. |
| **Overfitting** | Model memorizes training data and fails to generalize. |
| **Underfitting** | Model is too simple to learn meaningful patterns. |
| **Software Integration** | ML models must be integrated into production software. |
| **Offline Learning Challenges** | Updating deployed models requires retraining and redeployment. |
| **Deployment Challenges** | Deploying ML models on cloud platforms introduces engineering complexity. |
| **High Costs** | Large-scale ML systems require significant infrastructure investment. |
| **MLOps** | Helps manage deployment, monitoring, operations, and costs. |

## 4. Key Concepts
- Data Collection (APIs, Web Scraping)
- Labeled and Unlabeled Data
- Data Quality
- Sampling Noise and Bias
- Data Cleaning and Preprocessing
- Feature Engineering
- Garbage In, Garbage Out (GIGO)
- Overfitting and Underfitting
- Software Integration
- Model Deployment (Offline Learning, Cloud Deployment)
- MLOps

## 5. Important Definitions
- **Data Collection**: The process of gathering data required for training Machine Learning models.
- **Labeled Data**: Data for which the correct output or target value is already known.
- **Sampling Noise**: Random variation introduced during the data sampling process.
- **Sampling Bias**: A systematic error where the collected sample does not accurately represent the overall population.
- **Feature Engineering**: The process of selecting, modifying, or combining features to improve model performance.
- **Garbage In, Garbage Out (GIGO)**: The principle that poor-quality input data leads to poor-quality model predictions.
- **Overfitting**: A situation where the model memorizes the training data instead of learning generalizable patterns.
- **Underfitting**: A situation where the model is too simple to capture the underlying relationships in the data.
- **Software Integration**: The process of incorporating a Machine Learning model into software applications.
- **MLOps (Machine Learning Operations)**: A discipline focused on deploying, monitoring, maintaining, and managing Machine Learning systems in production.

## 6. Algorithms / Workflows
### A. Typical Machine Learning Project Workflow
1. Collect data.
2. Label the data (if required).
3. Clean and preprocess the data.
4. Perform feature engineering.
5. Train the Machine Learning model.
6. Evaluate the model.
7. Integrate the model into software.
8. Deploy the model.
9. Monitor performance and operational costs.
10. Update and maintain the deployed system.

### B. Data Preparation Workflow
1. Collect raw data.
2. Handle missing values.
3. Remove errors and noise.
4. Select relevant features.
5. Create useful derived features.
6. Prepare the dataset for model training.

## 7. Examples
**Example 1: Data Labeling**
For an image classification problem:
- Images containing cats are labeled as Cat.
- Images containing dogs are labeled as Dog.

The lecture highlights that manually labeling large datasets is a tedious and time-consuming process.

**Example 2: Overfitting**
A model closely fits every training data point.
- *Result*: Excellent performance on training data, poor performance on previously unseen data.

**Example 3: Underfitting**
A model is too simple to capture the underlying relationships.
- *Result*: Poor performance even on the training dataset.

**Example 4: Software Integration**
A trained Machine Learning model must be incorporated into applications such as websites or mobile applications. Compatibility across different operating systems, web environments, and programming languages presents additional engineering challenges.

## 8. Best Practices and Tips
- Prioritize collecting high-quality, representative datasets before focusing on model selection.
- Recognize that obtaining and labeling data is often one of the most resource-intensive stages of a Machine Learning project.
- Invest significant effort in data cleaning and preprocessing, as poor-quality data directly affects model performance.
- Apply feature engineering to remove irrelevant features and improve predictive capability.
- Monitor models for both overfitting and underfitting to ensure good generalization.
- Plan for software integration and deployment early in the project lifecycle rather than treating them as afterthoughts.
- Consider operational costs when deploying Machine Learning systems at scale.
- Use MLOps practices to streamline deployment, monitoring, maintenance, and cost management.

## 9. Key Takeaways
- Building successful Machine Learning systems involves much more than choosing an algorithm; data, engineering, deployment, and operations all play critical roles.
- Real-world data collection is significantly more challenging than working with pre-packaged datasets.
- Large, well-labeled datasets are valuable, but acquiring and labeling them is often expensive and time-consuming.
- Models trained on non-representative or poor-quality data produce unreliable predictions.
- Effective feature engineering is essential, while irrelevant features can degrade model performance (Garbage In, Garbage Out).
- Overfitting occurs when a model memorizes the training data, whereas underfitting occurs when the model is too simple to learn meaningful patterns.
- Machine Learning models must be integrated into software applications and deployed to production environments, introducing additional engineering complexity.
- Offline model updates and large-scale deployment present operational challenges, particularly in cloud environments.
- Running Machine Learning systems at scale can incur substantial infrastructure costs, making MLOps an important discipline for managing deployment, monitoring, and operational efficiency.
