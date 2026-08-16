# 1. Title
**ML Development Life Cycle (ML DLC) — Introduction & Overview**

## 2. Overview
The Machine Learning Development Life Cycle (ML DLC) is the machine-learning equivalent of the Software Development Life Cycle (SDLC). It provides a structured approach for building ML-based software products, from defining the problem to deployment, testing, optimization, and maintenance.

The lifecycle covers the complete process of developing an ML product rather than focusing only on training a model. The exact number and naming of stages may vary across different sources because ML engineering is still an evolving field. This framework uses 9 major steps as an organizing structure.

## 3. Detailed Notes

### 3.1 Why ML DLC Matters
- Earlier ML learning often focuses on what machine learning is and why it is used. ML DLC focuses on how to build an ML-based product.
- ML DLC provides a roadmap for developing ML products from the initial idea to the final deployed product.
- SDLC provides guidelines for building traditional software products from start to finish. ML DLC extends this idea to ML-based software.
- ML DLC is important for understanding end-to-end ML product development, rather than stopping after training a model and obtaining an accuracy score.
- Companies generally require ML engineers to understand the complete product-development process, including deployment and maintenance.
- The lifecycle is commonly organized into several stages, although the exact number and naming can differ between sources.

### 3.2 Step 1: Problem Framing
The first step is to clearly define the problem and determine what needs to be built.
**Important questions include:**
- What exactly needs to be solved?
- What does the customer need?
- What will the project cost?
- How large should the team be?
- What will the final product look like?
- Will the ML approach be supervised or unsupervised?
- Which type of algorithm may be suitable?
- Will the solution be deployed as an app or on the web?
- Where will the required data come from?

The goal is to develop a clear conceptual understanding of the problem and the required solution before moving forward.

### 3.3 Step 2: Data Collection
Machine learning requires data. In practice projects, data may already be available, but company projects often require collecting data specifically for the problem.

**Common data sources include:**
- **CSV files** — Data can be used directly when it is already available in the required format.
- **APIs** — Data can be retrieved from API endpoints using Python. APIs commonly return data in JSON format, which can then be converted into another preferred format such as CSV.
- **Web scraping** — Data can be collected directly from websites when suitable files or APIs are unavailable.
- **Databases** — Data may exist in databases, but ML workflows generally avoid directly working with live production databases. A Data Warehouse can be used instead.
  - The process of extracting, transforming, and loading data into a warehouse is known as **ETL (Extract, Transform, Load)**.
- **Big Data platforms** — Cluster-based technologies such as Spark can be used when the volume of data is extremely large.

Properly collecting and storing the required data is essential because subsequent ML stages depend on it.

### 3.4 Step 3: Data Preprocessing
Newly collected data is often unclean or "dirty" and cannot be used directly for model training. Data preprocessing involves preparing the data before it is supplied to the ML algorithm.

**Common problems include:**
- Duplicate entries
- Missing values
- Outliers
- Data from different sources that does not align correctly
- Features with significantly different numerical scales

**Common preprocessing tasks include:**
- Removing duplicates
- Handling missing values
- Removing or handling outliers
- Scaling numerical features
  - *Scaling is useful when different input columns contain values on very different scales. Bringing features to comparable scales prevents large-valued features from disproportionately affecting calculations used by certain ML algorithms.*

The overall objective is to transform raw data into a clean and usable format.

### 3.5 Step 4: Exploratory Data Analysis (EDA)
Exploratory Data Analysis (EDA) is used to understand the data and discover relationships between inputs and outputs before building a model. EDA involves performing experiments and using visualizations to understand patterns within the dataset.

**Three common types of analysis are:**
- **Univariate Analysis** — Examining one column independently to understand its distribution and patterns.
- **Bivariate Analysis** — Examining two columns together to understand their relationship.
- **Multivariate Analysis** — Examining three or more columns together to understand relationships among multiple variables.

EDA also includes identifying and handling imbalanced datasets.
*For example, in a Dog vs. Cat image-classification problem, a dataset containing significantly more cat images than dog images would be imbalanced.*

Thorough data analysis at this stage makes later modeling decisions easier.

### 3.6 Step 5: Feature Engineering and Feature Selection
Features are the input columns used by an ML model.

**Feature Engineering**
Feature engineering involves creating new features or modifying existing features to make the modeling process more effective or simpler.
*For example, in a house-price prediction problem, the number of rooms and number of bathrooms might individually provide limited information about the price. These inputs could potentially be replaced or transformed into a more useful feature such as Square Feet, depending on the available data and problem context.*
Feature engineering involves using domain understanding and judgment to create useful representations of the data.

**Feature Selection**
A dataset may contain many features, but not every feature contributes useful information to the output.
Unhelpful features can be removed because:
- They may not meaningfully affect the output.
- A larger number of features can increase model-training time.

Feature engineering and feature selection are important parts of preparing data for effective model training.

### 3.7 Step 6: Model Training
Once the data has been cleaned and useful features have been prepared, the next step is model training.
Instead of relying on only one algorithm, multiple algorithms from different algorithm families can be trained on the same dataset. Different algorithms can perform differently depending on the characteristics of the data. Therefore, several candidate algorithms are trained and compared before deciding which approach is most suitable.

### 3.8 Step 7: Model Evaluation
After training multiple models, their performance needs to be compared. This is done using performance metrics.

**Different types of problems require different evaluation metrics, including:**
- Classification metrics
- Regression metrics

The evaluation results help determine which models perform best on the given problem.

### 3.9 Step 8: Model Selection
After evaluating the trained models, one or more suitable models are selected. The selected model can then be improved by adjusting its hyperparameters.

**Hyperparameter tuning** involves adjusting the settings that control how a model operates in order to improve its performance.
*An analogy is adjusting settings on a TV, such as picture mode or volume, depending on what is being watched. Similarly, model settings can be adjusted according to the requirements of the ML problem.*

### 3.10 Step 9: Ensemble Learning
Ensemble Learning involves combining multiple ML models or algorithms to create a more powerful model.

**Common ensemble techniques include:**
- Bagging
- Boosting
- Stacking

The general idea is to combine multiple models rather than relying on a single model. The resulting ensemble can provide improved performance compared with individual models in suitable situations.

### 3.11 Deployment
Training a model does not complete the ML development process. The trained model needs to be converted into usable software so that users can interact with it through a website, mobile application, or desktop application.

**A typical deployment flow is:**
1. Convert the trained model into a serialized or binary file.
2. Wrap the model in an API.
3. Connect the API to the application's backend.
4. Accept user input through the frontend.
5. Send the input to the server.
6. Load the trained model and generate a prediction.
7. Return the prediction to the frontend in an appropriate format such as JSON.
8. Host the application and model on a cloud platform such as AWS or GCP (Google Cloud Platform).

Deployment therefore requires both ML and software-engineering components, including frontend and backend development.

### 3.12 Testing
After deployment, the system can undergo Beta Testing.
Beta testing involves releasing a new model or feature to a smaller group of trusted users before making it available to everyone. The purpose is to collect feedback and identify potential problems.

If the model performs well and feedback is positive, the system can proceed toward wider deployment. If problems are discovered, earlier stages may need to be revisited.
**Possible problems can originate from:**
- Data collection
- Data preprocessing
- Feature selection
- Algorithm selection
- Model performance

### 3.13 Optimization, Full-Scale Deployment, and Maintenance
After successful testing, the model can be released to all users.
Several operational practices are important at this stage:
- **Model backup** — Maintain previous versions so the system can be restored if necessary.
- **Data backup** — Preserve important data for recovery and rollback.
- **Load balancing** — Distribute requests across resources when the number of users or requests increases.
- **Retraining frequency** — Determine how often the model should be retrained.
- **Automation** — Automate the retraining and maintenance process instead of performing these tasks manually.
- **Optimization** — Identify unnecessary costs and inefficiencies throughout the ML pipeline.

A model can become less effective over time when real-world data patterns change. This degradation is referred to in the material as model "rot"/degradation. Periodic retraining can help maintain model performance.
*For example, a mask-detection model may become less accurate if the ways people wear masks change over time. The model may therefore need to be retrained using newer data.*

Maintenance is an ongoing part of real-world ML development.

## 4. High-Level ML DLC Workflow
1. **Problem Framing** — Define the problem, requirements, cost, team, product type, ML approach, algorithm type, platform, and data source.
2. **Data Collection** — Gather data from CSV files, APIs, web scraping, databases/data warehouses, or big-data platforms.
3. **Data Preprocessing** — Clean the data by handling duplicates, missing values, outliers, and feature scaling.
4. **Exploratory Data Analysis (EDA)** — Analyze the data using univariate, bivariate, and multivariate analysis and identify issues such as class imbalance.
5. **Feature Engineering & Selection** — Create useful features and remove unnecessary features.
6. **Model Training** — Train multiple algorithms from different families.
7. **Model Evaluation** — Compare trained models using appropriate performance metrics.
8. **Model Selection** — Select suitable models and tune their hyperparameters.
9. **Ensemble Learning (Optional)** — Combine multiple models using techniques such as bagging, boosting, or stacking.
10. **Deployment** — Serialize the model, expose it through an API, connect it to a frontend, and host it on a server or cloud platform.
11. **Testing** — Perform beta testing with a smaller group of users and collect feedback.
12. **Optimization & Maintenance** — Roll out the system fully, maintain backups, handle load balancing, establish retraining schedules, automate maintenance, and optimize the overall pipeline.

> *The material describes these stages as a 9-step organizing framework, while the detailed workflow naturally expands into additional sub-stages.*

## 5. Important Definitions
- **SDLC (Software Development Life Cycle):** Guidelines followed to build a software product from start to finish.
- **ML DLC (Machine Learning Development Life Cycle):** Guidelines for developing ML-based software products from the initial idea through deployment and maintenance.
- **ETL (Extract, Transform, Load):** A process for extracting, transforming, and loading data into a data warehouse.
- **Feature:** An input column used by an ML model.
- **Feature Engineering:** Creating or modifying features to make modeling more effective.
- **Feature Selection:** Removing features that do not provide useful information or unnecessarily increase training time.
- **Univariate Analysis:** Analysis of a single column.
- **Bivariate Analysis:** Analysis of two columns and their relationship.
- **Multivariate Analysis:** Analysis involving three or more columns.
- **Imbalanced Dataset:** A dataset in which one class has significantly more examples than another.
- **Hyperparameter Tuning:** Adjusting model settings to improve performance.
- **Ensemble Learning:** Combining multiple models to create a more powerful model.
- **Beta Testing:** Testing a model or feature with a smaller group of users before a full rollout.
- **Model Rot/Degradation:** Declining model performance over time as real-world data patterns change.

## 6. Examples
**House Price Prediction**
Separate features such as the number of rooms and bathrooms can potentially be transformed into a more useful feature such as Square Feet, depending on the problem and available data.

**Image Classification**
A Dog vs. Cat dataset containing far more cat images than dog images represents an imbalanced dataset that may require appropriate handling.

**Mask Detection**
A mask-detection model may become outdated when real-world patterns change, requiring periodic retraining.

**Hyperparameter Tuning**
Hyperparameter tuning can be compared to adjusting TV settings according to viewing requirements.

**EDA and Preparation**
The tree-cutting analogy illustrates the importance of preparation: spending more time preparing the tools can reduce the effort required for the main task. Similarly, spending sufficient time understanding the data can make later modeling decisions easier.

**Beta Testing**
A new feature can first be released to a smaller group of trusted users to collect feedback before a full rollout.

## 7. Best Practices
- Spend sufficient time on EDA to understand the data before making modeling decisions.
- Train multiple algorithms instead of assuming one algorithm will perform best.
- Remove features that do not meaningfully contribute to the output.
- Automate retraining and maintenance processes.
- Use beta testing before a full rollout.
- Back up both the model and data so that previous working versions can be restored when necessary.
- Continuously monitor and optimize the deployed ML system.

## 8. Key Takeaways
- ML DLC is the machine-learning equivalent of SDLC and provides a structured approach to building ML-based software.
- ML development extends far beyond model training. It includes problem framing, data collection, preprocessing, EDA, feature engineering and selection, training, evaluation, model selection, deployment, testing, and maintenance.
- EDA and feature engineering/selection are particularly important because they strongly influence later modeling decisions.
- Multiple algorithms and models should be evaluated because no single algorithm is guaranteed to perform best for every dataset.
- Deployment converts the trained model into a usable software component that can interact with a frontend through an API.
- Testing, backups, load balancing, retraining, automation, and optimization are essential parts of maintaining a production ML system.
- ML development is an ongoing lifecycle rather than a process that ends when a model is trained.
