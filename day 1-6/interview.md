# Machine Learning Fundamentals: Interview Questions (Days 1-6)

This document contains 20 interview questions based on the fundamental concepts covered in Days 1 through 6 of the Machine Learning course.

---

### Q1: Can you explain the hierarchy and differences between Artificial Intelligence, Machine Learning, and Deep Learning?
<details>
<summary>View Answer</summary>

They can be visualized as nested subsets:
- **Artificial Intelligence (AI)** is the broadest concept. It is the science of creating machines that exhibit human-like intelligence.
- **Machine Learning (ML)** is a subset of AI. Instead of using manually programmed rules, ML uses statistical techniques to automatically discover patterns and learn from data.
- **Deep Learning (DL)** is a specialized subset of ML. It relies on Artificial Neural Networks (ANNs) inspired by the human brain and is particularly powerful at automatically extracting features from large, complex, and unstructured datasets (like images or text).
</details>

### Q2: What is Symbolic AI (or an Expert System), and what are its primary limitations compared to Machine Learning?
<details>
<summary>View Answer</summary>

Symbolic AI (or Knowledge-Based AI) is an early approach where human experts manually converted their knowledge into explicit, hard-coded rules for the computer to follow. 
Its primary limitation is that it only works well for closed, well-defined problems. It struggles with complex, highly variable real-world scenarios (like recognizing a dog in a photo) because it is virtually impossible to manually write rules covering every possible variation in size, shape, lighting, and pose. Machine Learning overcomes this by learning patterns directly from data.
</details>

### Q3: How does Deep Learning reduce the need for manual "Feature Engineering"?
<details>
<summary>View Answer</summary>

In traditional Machine Learning, practitioners must perform manual "Feature Engineering"—identifying and extracting the most important characteristics (features) from the raw data before feeding it to the algorithm. 
Deep Learning solves this by performing **Automatic Feature Extraction**. Through its multiple layers of neural networks, the model learns the most relevant features directly from the raw data on its own, making it highly effective for unstructured data.
</details>

### Q4: Compare Supervised Learning and Unsupervised Learning. What kind of problem does each solve?
<details>
<summary>View Answer</summary>

- **Supervised Learning** requires training data that includes both the input features and the correct output labels. The model learns the mapping from inputs to outputs. It is used for *Regression* (predicting continuous numerical values) and *Classification* (predicting categorical classes).
- **Unsupervised Learning** uses data that only contains inputs, with no known output labels. The model's goal is to discover hidden patterns or structures in the data. Common techniques include *Clustering* (grouping similar data points), *Dimensionality Reduction*, and *Anomaly Detection*.
</details>

### Q5: Describe the core components and process of Reinforcement Learning.
<details>
<summary>View Answer</summary>

Reinforcement Learning is a paradigm where an **Agent** learns through trial and error by interacting with an **Environment**. 
The process works as a feedback loop: The agent performs actions in the environment, and the environment responds by providing feedback in the form of **Rewards** (for good actions) or **Punishments** (for bad actions). The agent continuously updates its strategy to maximize its total cumulative reward.
</details>

### Q6: What is the fundamental difference between Batch Learning and Online Learning?
<details>
<summary>View Answer</summary>

- **Batch Learning (Offline Learning)** trains the model all at once using the entire available dataset. Once deployed, the model is static and cannot learn from new data unless it is taken offline, merged with new data, and completely retrained from scratch.
- **Online Learning** allows the model to learn incrementally. As new data arrives in production, the deployed model continuously updates itself in real-time or near real-time without needing to be retrained from scratch.
</details>

### Q7: What is "Concept Drift," and which learning approach is best suited to handle it?
<details>
<summary>View Answer</summary>

Concept Drift occurs when the underlying statistical properties or patterns in the data change over time (e.g., shifts in consumer behavior). 
**Online Learning** is best suited to handle concept drift because the model is continuously updated with the latest incoming data, allowing it to adapt quickly. A Batch Learning model would suffer from "model stagnation" and serve outdated predictions.
</details>

### Q8: If you have a dataset that is terabytes in size and cannot fit into your machine's RAM, how would you train a machine learning model on it?
<details>
<summary>View Answer</summary>

You would use a technique called **Out-of-Core Learning**. Since the entire dataset cannot be loaded into memory at once, the data is split into smaller, manageable batches. The model loads one batch into RAM at a time, trains incrementally on that batch, and then discards it to load the next batch. This relies on incremental learning algorithms.
</details>

### Q9: Contrast Instance-Based Learning with Model-Based Learning.
<details>
<summary>View Answer</summary>

- **Instance-Based Learning (Lazy Learning)** does not build a generalized mathematical model during training. It simply memorizes the training dataset. Predictions are made by comparing a new input to the stored instances and finding the most similar ones. It requires a lot of storage and can be slow at prediction time.
- **Model-Based Learning** analyzes the training data to learn a generalized mathematical relationship or "decision boundary." The original data can then be discarded, keeping only the learned model parameters. Predictions are fast.
</details>

### Q10: How does the K-Nearest Neighbors (KNN) algorithm work, and which learning paradigm does it belong to?
<details>
<summary>View Answer</summary>

KNN works by storing all the training data. For a new data point, it calculates the distance between the new point and all stored points, identifies the "K" closest neighbors, and bases its prediction on their outcomes (e.g., taking the majority class).
It is a classic example of **Instance-Based Learning** because it relies entirely on memorizing the training examples to make predictions.
</details>

### Q11: What are some typical real-world use cases for Supervised Classification versus Unsupervised Clustering?
<details>
<summary>View Answer</summary>

- **Supervised Classification:** Spam detection in emails (labeling as Spam/Not Spam), disease diagnosis based on medical records, or image recognition (identifying if an image contains a cat or a dog). These rely on historical labeled data.
- **Unsupervised Clustering:** Customer segmentation for targeted marketing, identifying housing sub-markets based on location and price, or grouping related news articles. These operate without prior labels, looking for natural groupings.
</details>

### Q12: What are the main disadvantages of using an Instance-Based algorithm like KNN in production?
<details>
<summary>View Answer</summary>

The main disadvantages are:
- **Storage cost:** It requires keeping the entire training dataset in memory to make predictions.
- **Prediction speed:** It can be extremely slow at inference time, because it must calculate the distance between the new data point and every single stored instance in the dataset.
- **Curse of dimensionality:** Distance metrics become less meaningful and computations become more expensive when dealing with a high number of features.
</details>

### Q13: What is "Model Stagnation" and in what learning context does it usually occur?
<details>
<summary>View Answer</summary>

Model Stagnation occurs when a deployed model's predictive performance degrades over time because the real-world data distribution changes (Concept Drift), but the model itself remains static. This is primarily a problem associated with **Batch Learning**, where the model cannot learn from new data without a complete retraining cycle.
</details>

### Q14: Beyond Clustering, what are two other common Unsupervised Learning techniques, and what are their purposes?
<details>
<summary>View Answer</summary>

- **Dimensionality Reduction:** The goal is to simplify data without losing too much information, merging strongly correlated features. It's often used to speed up models or visualize high-dimensional data.
- **Anomaly Detection (or Novelty Detection):** The goal is to identify rare, unusual data points that deviate significantly from the majority of the data. This is heavily used in fraud detection or detecting manufacturing defects.
</details>

### Q15: How do Regression and Classification differ in terms of their expected outputs? Give an example for each.
<details>
<summary>View Answer</summary>

- **Regression** predicts a continuous numerical value. Example: Predicting the price of a house based on its square footage and location.
- **Classification** predicts a discrete categorical label (a class). Example: Predicting whether a bank transaction is "Fraudulent" or "Legitimate".
</details>

### Q16: Deep Learning automates feature engineering, but what are its main drawbacks compared to traditional Machine Learning?
<details>
<summary>View Answer</summary>

The primary drawbacks of Deep Learning are:
- **Data hungry:** It typically requires massive amounts of labeled data to perform well and avoid overfitting.
- **Computational cost:** Training Deep Learning models (like ANNs) is computationally expensive, often requiring specialized hardware like GPUs.
- **Interpretability:** DL models are often considered "black boxes," making it very difficult to understand *why* they made a specific prediction, compared to more transparent traditional models like Decision Trees.
</details>

### Q17: In the context of Reinforcement Learning, what is the Exploration vs. Exploitation trade-off?
<details>
<summary>View Answer</summary>

- **Exploration** involves the agent trying new, untested actions to discover more about the environment and potentially find higher long-term rewards.
- **Exploitation** involves the agent relying on its current knowledge to choose the action that it *already knows* yields the highest immediate reward.
The trade-off is finding the right balance: exploring enough to find the optimal strategy without wasting too much time on bad actions, while exploiting known good actions to maximize total rewards.
</details>

### Q18: Provide an example of a scenario where Online Learning is practically mandatory rather than just a nice-to-have optimization.
<details>
<summary>View Answer</summary>

High-frequency trading algorithms in financial markets. Market dynamics shift minute-by-minute, and a model trained on last week's or even yesterday's data (Batch Learning) would be instantly obsolete and lose money. The system *must* continuously ingest new tick data and update its strategy (Online Learning) to remain profitable. Similarly, massive dynamic platforms like YouTube's recommendation engine rely on continuous online learning to react to trending videos instantly.
</details>

### Q19: Compare the computational profile (Training vs. Inference time) of Model-Based Learning compared to Instance-Based Learning.
<details>
<summary>View Answer</summary>

- **Model-Based Learning:** Computationally heavy and slow during the *training phase* (as it optimizes parameters to find the best decision boundary), but extremely fast during *inference* (prediction time) because it only involves passing the input through a fixed mathematical formula.
- **Instance-Based Learning:** Extremely fast (or zero) time during the *training phase* (it simply stores the data), but computationally heavy and slow during *inference* because it must compare the new point against all stored instances.
</details>

### Q20: Why did the AI industry shift away from Symbolic AI (Expert Systems) for tasks like Natural Language Processing (NLP) or Computer Vision?
<details>
<summary>View Answer</summary>

The shift occurred because human language and visual data are full of nuances, exceptions, edge cases, and ambiguity. Symbolic AI required human experts to hard-code every possible rule to handle these variations, which proved impossible to scale. Machine Learning shifted the paradigm by allowing computers to automatically infer these complex patterns and statistical probabilities directly from massive amounts of text or image data, far outperforming manually crafted rules.
</details>
