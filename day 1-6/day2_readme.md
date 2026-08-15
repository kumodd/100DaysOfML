# AI vs. Machine Learning (ML) vs. Deep Learning (DL)

## Overview
This lecture explains the relationship and differences between Artificial Intelligence (AI), Machine Learning (ML), and Deep Learning (DL). It introduces AI as the broad concept of creating intelligent machines, explains the limitations of early Symbolic AI (Knowledge-based AI), describes how Machine Learning overcomes these limitations by learning patterns from data, and finally explains how Deep Learning extends Machine Learning through artificial neural networks and automatic feature extraction. The lecture concludes with a comparison of ML and DL, highlighting their strengths and ideal use cases.

## Detailed Notes

### Introduction
The lecture addresses one of the most common beginner questions: **What is the difference between AI, ML, and DL?**

The relationship between the three concepts can be visualized as nested circles:
- **Artificial Intelligence (AI)** → Largest circle
- **Machine Learning (ML)** → Subset of AI
- **Deep Learning (DL)** → Subset of ML

**Hierarchy**
```text
Artificial Intelligence (AI)
│
└── Machine Learning (ML)
      │
      └── Deep Learning (DL)
```

### Artificial Intelligence (AI)
**Definition**
Artificial Intelligence (AI) is the concept of creating intelligence in machines.

**What is Intelligence?**
According to the lecture, human intelligence consists of a combination of abilities, including:
- Logic
- Coding
- Problem-solving
- Creativity
- Imagination
- Emotional intelligence

**Current State of AI**
The broader vision is to build **Artificial General Intelligence (AGI)**. However, most current AI systems are:
- Goal-oriented
- Designed for specific tasks
- Not focused on creativity or imagination

### Historical Background of AI
**Beginning of AI**
The concept of machine intelligence began around the 1950s.

**Symbolic AI (Knowledge-based AI)**
One of the earliest approaches to AI was:
- Symbolic AI
- Knowledge-based AI
- Expert Systems

**How Symbolic AI Worked**
- Human experts manually converted their knowledge into rules.
- These rules were programmed into computers.
- *Example: Chess*
  - A chess expert writes down strategies and rules.
  - These rules are encoded into the computer.
  - The computer follows these predefined rules while playing chess.

**Limitations of Symbolic AI**
Symbolic AI worked only for:
- Closed problems
- Well-defined domains
- Problems where rules could be explicitly written

It struggled with problems involving:
- Large variation in data
- Complex real-world scenarios

*Example: Dog Recognition*
For image recognition, manually writing rules becomes impractical because dogs appear in different:
- Sizes
- Shapes
- Colors
- Poses
- Lighting conditions

Writing rules for every possible variation is effectively impossible. This limitation led to the development of Machine Learning.

### Machine Learning (ML)
**Definition**
Machine Learning is a branch of computer science where statistical techniques are used to discover patterns in data.

**Key Difference from Symbolic AI**
Instead of explicitly programming rules:
- Data is provided to the algorithm.
- The algorithm discovers patterns automatically.
- These learned patterns become the basis for predictions or classifications.

**Machine Learning Workflow**
1. Collect data.
2. Feed data into the learning algorithm.
3. The algorithm identifies statistical patterns.
4. The learned model is used for prediction or classification.

**Example: Dog Classification**
Instead of manually defining rules such as ear shape, tail shape, and body characteristics, the ML system is shown thousands of dog images, allowing it to learn how to distinguish dogs from the data itself.

### Deep Learning (DL)
**Definition**
Deep Learning is a specialized subset of Machine Learning based on Artificial Neural Networks (ANNs).

**Learning Procedure**
The overall process is similar to Machine Learning:
- Provide data
- Train the algorithm

The primary difference lies in the underlying model architecture.

**Artificial Neural Networks**
Deep Learning is inspired by biological neural networks. The implementation is a mathematical model, not a biological replica.

### Why Deep Learning Became Popular
**Limitation of Traditional Machine Learning**
A major challenge in conventional ML is manual feature engineering. Before training, the user often needs to define important characteristics (features).

*Example*: For dog recognition, features might include ear shape and tail shape. The quality of these manually selected features directly affects model performance.

**Automatic Feature Extraction**
Deep Learning removes much of the need for manual feature engineering. Instead:
- The neural network automatically learns useful features from the data.
- This capability is especially valuable for complex, unstructured data.

**Effect of Increasing Layers**
Adding more layers of neurons improves the network's ability to:
- Learn complex representations
- Predict accurately
- Perform classification tasks more effectively

### Data Requirements
**Deep Learning**
Deep Learning performs particularly well when trained on large datasets. As additional data becomes available, performance continues improving.

**Machine Learning**
Machine Learning models improve initially with more data, but eventually:
- Performance stabilizes.
- Additional data produces diminishing improvements.

### Applications
**Deep Learning**
The lecture mentions DL being widely used for:
- Image classification
- Text-related tasks

**Machine Learning**
Machine Learning remains preferable when available datasets are small. Examples of such domains include:
- Banking
- Insurance

### Comparison: AI vs. ML vs. DL

| Aspect | Artificial Intelligence (AI) | Machine Learning (ML) | Deep Learning (DL) |
| :--- | :--- | :--- | :--- |
| **Definition** | Creating intelligence in machines | Learning patterns from data using statistical techniques | Machine Learning using artificial neural networks |
| **Relationship** | Broadest field | Subset of AI | Subset of ML |
| **Rule Creation** | May involve manually designed rules (e.g., Symbolic AI) | Learns rules from data | Learns rules and features from data |
| **Programming** | Can rely on explicit programming | No explicit rule programming | No explicit rule programming |
| **Feature Engineering** | Not specifically discussed | Manual feature definition required | Features learned automatically |
| **Architecture** | General AI methods | Statistical learning algorithms | Artificial neural networks |
| **Data Requirement**| Not discussed | Effective on smaller datasets | Performs best with large datasets |
| **Typical Applications**| General intelligent systems | Banking, Insurance | Image classification, Text-related tasks |

### Evolution of AI Approaches
```text
Artificial Intelligence
        │
        ▼
Symbolic AI (Expert Systems)
        │
        │  Manual Rules
        ▼
Machine Learning
        │
        │  Learns Patterns from Data
        ▼
Deep Learning
        │
        │  Learns Features + Patterns Automatically
        ▼
Better performance on complex data
```

## Key Concepts
- **Artificial Intelligence (AI)**
- **Artificial General Intelligence (AGI)**
- **Machine Learning (ML)**
- **Deep Learning (DL)**
- **Symbolic AI** (Knowledge-based AI / Expert Systems)
- Statistical pattern recognition
- Artificial Neural Networks (ANNs)
- Manual feature engineering
- Automatic feature extraction
- Image classification / Text-related tasks
- Large vs. small dataset suitability

## Important Definitions
- **Artificial Intelligence (AI)**: The concept of creating intelligence in machines.
- **Machine Learning (ML)**: A branch of computer science that uses statistical techniques to learn patterns from data instead of relying on explicitly programmed rules.
- **Deep Learning (DL)**: A specialized subset of Machine Learning that uses artificial neural networks to automatically learn features and patterns from data.
- **Symbolic AI (Knowledge-based AI)**: An early AI approach in which human experts manually encoded knowledge and decision rules into computer systems.
- **Artificial Neural Network (ANN)**: A mathematical model inspired by biological neural networks that forms the foundation of Deep Learning.
- **Feature Engineering**: The manual process of defining important characteristics (features) that a Machine Learning model uses for learning.
- **Automatic Feature Extraction**: The ability of Deep Learning models to learn useful features directly from raw data without manual specification.

## Algorithms / Workflows

### A. Symbolic AI Workflow
1. Human experts identify knowledge.
2. Knowledge is converted into explicit rules.
3. Rules are programmed into the computer.
4. The computer follows those rules to solve the task.

### B. Machine Learning Workflow
1. Collect data.
2. Feed the data into the learning algorithm.
3. The algorithm discovers statistical patterns.
4. The trained model performs prediction or classification.

### C. Deep Learning Workflow
1. Collect large amounts of data.
2. Train an artificial neural network.
3. The network automatically learns features.
4. Deeper layers improve representation learning.
5. The trained model performs prediction or classification.

## Examples
- **Example 1: Chess (Symbolic AI)**
  - A chess expert converts strategies into rules.
  - Those rules are programmed into a computer.
  - The computer follows the predefined rules to play chess.

- **Example 2: Dog Recognition (Machine Learning)**
  - Instead of manually writing recognition rules, thousands of dog images are provided.
  - The system learns to classify dogs by identifying patterns in the training data.

- **Example 3: Feature Engineering vs. Automatic Feature Learning**
  - *Traditional Machine Learning*: The user manually specifies features such as ear shape and tail shape.
  - *Deep Learning*: The neural network automatically learns relevant features from the training data.

## Best Practices and Tips
- View AI, ML, and DL as a hierarchy: **AI ⊃ ML ⊃ DL**.
- Use Machine Learning when working with smaller datasets.
- Use Deep Learning for complex, unstructured data, especially when large datasets are available.
- Avoid manually coding rules for highly variable real-world problems when data-driven learning approaches are more suitable.
- Recognize that Deep Learning reduces the need for manual feature engineering by learning features directly from data.

## Key Takeaways
- Artificial Intelligence is the broad field focused on creating intelligent machines.
- Machine Learning is a subset of AI that learns patterns from data instead of relying on manually programmed rules.
- Deep Learning is a specialized subset of Machine Learning built on artificial neural networks.
- Symbolic AI depended on expert-defined rules but struggled with complex, real-world problems due to the difficulty of encoding every possible rule.
- Machine Learning addressed this limitation by automatically learning patterns from data.
- Deep Learning further improved upon Machine Learning by automatically learning both features and patterns.
- Increasing the depth of neural networks improves predictive and classification capabilities.
- Deep Learning excels with large datasets and is widely used for image classification and text-related tasks.
- Traditional Machine Learning remains advantageous for applications with relatively small datasets, such as those commonly found in banking and insurance.
