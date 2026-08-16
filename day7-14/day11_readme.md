# 1. Title
**Tensors: The Fundamental Data Structure of Machine Learning**

## 2. Overview
This session (Day 10 of the "100 Days of Machine Learning" series) marks the first video in the series focused on the practical "how" of machine learning, rather than the "why" and "what" covered previously. The topic is **Tensors** — explained as the basic data structure underlying all major ML/DL libraries (scikit-learn, TensorFlow). 

The speaker builds up understanding from 0D tensors (scalars) through 1D (vectors), 2D (matrices), 3D, 4D, and 5D tensors, using NumPy code demonstrations and real-world practical examples (student placement data, NLP text vectorization, time series stock data, images, and videos) to illustrate where each dimensionality appears in real ML/DL work.

## 3. Detailed Notes

### 3.1 Why Study Tensors?
From this session onward, the speaker shifts focus from the "why" and "what" of ML to the "how" — practical machine learning.
**Why tensors specifically, first:** The short answer given is that a tensor is fundamentally a data structure — a way of storing data.

**Reasons tensors are important:**
- All leading ML/DL libraries today — scikit-learn, TensorFlow, etc. — use the tensor as their most basic data structure. Any ML or DL problem will require dealing with tensors.
- The speaker notes that Google's TensorFlow, described as the current number one deep learning library, is literally named after the tensor.
- Studying tensors today will help with both machine learning and deep learning going forward.

### 3.2 What Is a Tensor?
A tensor is nothing but a data structure — a way of storing data. More specifically, a tensor is described as a container for numbers. Occasionally characters can also be stored, but this is very rare — almost 99.99% of the time it will be a container for numbers.

The speaker notes that vectors and matrices — likely already familiar to viewers — are actually tensors:
- A single number (0-dimensional) is called a **scalar**.
- A list of numbers (1D) is called a **vector**.
- Numbers in 2D are called a **matrix**.
- For 3D, 4D, and beyond, there wasn't a common name, so scientists coined a general term and chose to call it **tensor**.

### 3.3 0D Tensor (Scalar)
A single number stored anywhere is called a scalar, or a 0D tensor.
"0D" means the tensor's number of dimensions is zero.

**NumPy demonstration:** Creating a scalar via `t = np.array()` with a single number inside, then printing `t` shows the scalar/0D tensor.
- Tensors and N-dimensional arrays (ndarray) are the same thing for those with a computer science background.
- To check a tensor's dimension in NumPy, use the `ndim` property. For a scalar, `ndim` returns 0, confirming it as a 0D tensor.

### 3.4 1D Tensor (Vector)
A list of numbers, e.g., `[1, 2, 3, 4]`, is a 1D tensor — also called a vector, or in programming terms, an N-dimensional array or simply an array. Its dimension (`ndim`) would be 1.

### 3.5 Axis, Rank, and Dimension
- **Axis:** basically represents how many directions your data has. If a tensor has 2 dimensions, it has two axes; a 3D tensor has three axes.
- Dimension and axis are related — however many "D" the tensor is, that's how many axes it has.
- **Rank:** another term for number of axes, and it is also equal to the tensor's dimension.
- **Key relationship stated explicitly:** Number of Axes = Rank = Dimension of the Tensor.

### 3.6 Creating a 1D Tensor in NumPy
**Code:** `np.array([1, 2, 3, 4])` (passing a Python list into `np.array`).
Printing `t` shows the 1D tensor; `t.ndim` shows dimension = 1, meaning number of axes = 1, rank = 1.

### 3.7 Important Distinction: Tensor Dimension vs. Vector Dimension
This is flagged by the speaker as a potentially confusing but important point.
- A 1D tensor is also called a vector. But if asked "what is the dimension of the vector," since there are, e.g., 4 numbers in it, the answer would be that this vector is 4D (4-dimensional).
- So although the tensor is 1D, the vector itself can be described as having as many dimensions as it has numbers.
- **Example:** `[1, 2]` is still a 1D tensor and also a vector, but if asked how many dimensions this vector has, the answer is 2, because it contains two numbers.
- **Mental model to retain:** whenever you create a 1D tensor, it is a vector, and that vector's own "dimensionality" equals however many numbers are inside it.

### 3.8 How Tensors Build Up (General Pattern)
If you keep adding scalars together, you get a vector — e.g., combining four scalars gives a vector.
General rule for how tensors grow: if you collect/combine tensors of the previous dimension, you get the next dimension up:
- A 1D tensor is basically a collection of multiple 0D tensors.
- A vector is a collection of scalars.
- A matrix is a collection of vectors.

### 3.9 2D Tensor (Matrix)
If you have multiple vectors and collect/combine them, the result is called a matrix.
- **Example:** combining vectors like `[1,2,3], [4,5,6], [7,8,9]` forms a matrix — a collection of vectors, with dimension 2D (two axes: a row axis and a column axis).

**NumPy demonstration:** Creating a matrix via `mat = np.array([[1,2,3],[4,5,6],[7,8,9]])`. Printing `mat` shows a 3×3 matrix; `ndim` returns 2, confirming it's a 2D tensor.

### 3.10 3D Tensor and Beyond (General Construction)
- To build a 3D tensor, take multiple matrices — e.g., if you have several 3×3 matrices and take 4 of them, you get a 4×3×3 tensor, called a 3D tensor, with 3 axes: a column axis, a row axis, and a depth axis.
- A 4D tensor is basically a collection of 3D tensors.
- A 5D tensor would be a matrix of 3D tensors (i.e., a collection structured further out).
- For most machine learning work, tensors will range from 0D to 5D.

### 3.11 Terminology: Rank, Axis, and Shape
- **Rank =** number of dimensions of the tensor = number of axes.
- **Shape:** describes how many items exist along a particular axis. Example: for a matrix with 2 rows and 3 columns, described as a "2 by 3" matrix — its shape is `(2, 3)`. Its `ndim`/rank would still be 2.
- **Size:** the total number of items in a tensor — calculated by multiplying all the numbers in the shape together.
  - Shape `(2,3)` → size = 6 items.
  - Exception: for a scalar, size is always equal to 1 (not 0).
  - For a 1D tensor, e.g., with shape `(3,)` — the shape is simply 3.

### 3.12 Practical Example 1: 1D Tensor — Student Placement Dataset
- **Example dataset:** student data with 4 columns — CGPA, IQ, State, and Placement.
- For a single student, say they have CGPA 8.2, IQ 119, from West Bengal (encoded as 0). The numbers are: `8.2, 119, 0`.
- This set of numbers is a 1D tensor, also called a vector. This tensor is 1D because it has only one axis. But the vector itself is 3-dimensional.
- **General rule stated:** When you get an ML dataset, each row is actually a 1D tensor and a vector.

### 3.13 Practical Example 2: 2D Tensor — Full Input Dataset (Matrix)
- A 2D tensor is basically a collection of 1D tensors.
- Continuing the student dataset example: each student's input data is a 3D vector/1D tensor. A collection of 10,000 such vectors becomes a matrix.
- This full input dataset can be written as a matrix, commonly denoted `X` in machine learning. It is a 2D tensor.
- The standalone Placement column (all 10,000 values) is itself a 10,000-dimensional vector, which is a 1D tensor.

### 3.14 Practical Example 3: 3D Tensors
**Example A — NLP (Natural Language Processing) / Text Vectorization**
- If working with text data, 3D tensors appear. Example: three input texts — "Hi Nitesh," "Hi Rahul," "Hi Ankit."
- Words are converted to vectors (Vectorization). E.g., `Hi → [1, 0, 0, 0]`.
- For the sentence "Hi Nitesh," this becomes a 2D tensor. With 3 such sentences, the resulting collection is a 3D tensor.

**Example B — Time Series Data**
- Example scenario: tracking a stock's highest price and lowest price daily for a full year → shape would be 365 by 2 (a 2D tensor).
- If you have 10 years of this same stock data, you now have 10 such 2D tensors → resulting tensor shape: `10 × 365 × 2`, which is a 3D tensor.

### 3.15 Practical Example 4: 4D Tensors — Images
- An image is basically a collection of pixels.
- For color images, three channels are used: R, G, B.
- Each channel is a 2D matrix; combining three such 2D tensors produces a 3D tensor representing one color image.
- If you take a batch of 50 such color images, the resulting tensor shape becomes `50 × 3 × 100 × 100` — this is a 4D tensor.
- **Practical relevance:** Convolutional Neural Networks (CNNs).

### 3.16 Practical Example 5: 5D Tensors — Videos
- A video is basically a series of images ("frames") shown in rapid succession.
- A 60-second video shot at 30 fps, in 480p resolution, in color.
- Total number of frames = `60 × 30 = 1,800` images.
- This full single video (1,800 frames, each 3×480×720) is already 4D data.
- If you then have a collection of 4 such videos, this collection becomes a 5D tensor.
- **Axes represent:** (1) how many videos, (2) how many images/frames in a single video, (3 & 4) the size of each image (height × width), and (5) how many color channels.

## 4. Key Concepts
- A tensor is fundamentally a data structure — a container for numbers — and is the core data structure used across ML/DL libraries like scikit-learn and TensorFlow.
- Tensors generalize the concepts of scalar (0D), vector (1D), and matrix (2D) to any number of dimensions.
- Number of Axes = Rank = Dimension of the Tensor.
- Higher-dimensional tensors are built from collections of lower-dimensional tensors.
- Important distinction: The dimension of a tensor (axes) vs. the dimension of a vector (values contained).
- In typical ML work, tensors range from 0D to 5D.
- Shape and Size are related but distinct: shape describes item counts per axis; size is the total item count.

## 5. Important Definitions
- **Tensor:** A container for numbers; equivalent to an N-dimensional array (ndarray).
- **0D Tensor / Scalar:** A single number; has zero dimensions/axes.
- **1D Tensor / Vector:** A list of numbers; has one axis/dimension.
- **2D Tensor / Matrix:** A collection of vectors; has two axes.
- **3D Tensor:** A collection of matrices; has three axes, including a "depth" axis (or "time axis").
- **4D Tensor:** A collection of 3D tensors.
- **5D Tensor:** A collection of 4D tensors.
- **Axis:** Represents a direction/dimension along which data varies in a tensor.
- **Rank:** Another term for the number of axes/dimensions of a tensor.
- **Shape:** Describes how many items exist along each axis of a tensor.
- **Size:** The total number of items in a tensor, calculated by multiplying all values in its shape together.
- **ndim:** A NumPy property used to check the number of dimensions of an array.
- **Vectorization:** The process of converting text into numbers/vectors.
- **Vocabulary:** The set of all unique words present in a given corpus.
- **Numerical Encoding:** Converting categorical values into numbers.
- **Time Series Data:** Data collected at regular, frequent time intervals.
- **X (in ML notation):** The symbol representing the matrix of all input column data across all rows in a dataset.

## 6. Algorithms / Workflows

### Creating Tensors in NumPy
1. Import the library: `import numpy as np`
2. Create a 0D tensor: `t = np.array(5)`, then check `t.ndim`.
3. Create a 1D tensor: `t = np.array([1, 2, 3, 4])`.
4. Create a 2D tensor: `mat = np.array([[1,2,3],[4,5,6],[7,8,9]])`.

### General Pattern for Building Higher-Dimensional Tensors
- Combine multiple 0D tensors (scalars) → get a 1D tensor (vector).
- Combine multiple 1D tensors (vectors) → get a 2D tensor (matrix).
- Combine multiple 2D tensors (matrices) → get a 3D tensor.
- Combine multiple 3D tensors → get a 4D tensor.
- Combine multiple 4D tensors → get a 5D tensor.

### Calculating Shape, Size, and Storage
1. Determine shape (items along each axis).
2. Multiply all shape values to get the size.
3. Multiply the total item count by the number of bits per item (e.g., 32 for float32).
4. Divide by 8 (to bytes), then 1024 (to KB), then 1024 (to MB) to estimate storage requirements.

## 7. Examples
- **0D Tensor:** `np.array(5)`.
- **1D Tensor:** `[1, 2, 3, 4]` or the vector `[8.2, 119, 0]` for a single student.
- **2D Tensor:** A 3×3 matrix `[[1,2,3],[4,5,6],[7,8,9]]` or the full student input matrix `X`.
- **3D Tensor (NLP):** Three sentences vectorized into a 3×2×4 tensor.
- **3D Tensor (Time Series):** 10 years of daily stock highest/lowest price data (10×365×2).
- **4D Tensor (Image):** A batch of 50 color images (50×3×100×100).
- **5D Tensor (Video):** A collection of 4 videos, each 60s long at 30fps in 480×720 color (4×1800×3×480×720).

## 8. Best Practices and Tips
- Check out NumPy tutorials/playlists for a refresher before proceeding.
- When learning tensors, keep clear the distinction between the dimension of the tensor itself (1D, 2D, etc.) and the dimension of a vector (based on how many numbers it contains).
- Use the `ndim` property in NumPy to verify dimensionality rather than assuming.
- When working with tabular ML data, recognize that you are simultaneously working with 1D tensors (individual rows, or output column) and 2D tensors (full input matrix `X`).

## 9. Key Takeaways
- A tensor is simply a container for numbers and is the fundamental data structure behind essentially all machine learning and deep learning libraries.
- Scalars, vectors, and matrices are just tensors of dimension 0, 1, and 2 respectively; the general term "tensor" extends this concept to any number of dimensions.
- Number of Axes = Rank = Dimension.
- Higher-dimensional tensors are always built as collections of the next-lower-dimensional tensor.
- A crucial distinction exists between a tensor's own dimensionality and a vector's "dimensionality" based on the count of numbers it holds.
- Real-world ML/DL data naturally maps onto different tensor dimensionalities: tabular data (1D/2D), NLP/time series (3D), images (4D), videos (5D).
- Most machine learning work involves tensors ranging from 0D to 5D; understanding shape and size calculations is essential for reasoning about data volume and storage requirements.
