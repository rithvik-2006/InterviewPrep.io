# Chapter 1: The Machine Learning Landscape – Revision Notes

This chapter serves as a high-level overview, introducing fundamental concepts and jargon in Machine Learning (ML).

---

## 1. What is Machine Learning?

* **Definition**: Machine Learning is about building systems that can **learn from data**, aiming to improve performance on a specific task, given a certain performance measure.
* **Learning Example**: A spam filter learns to flag spam emails using examples of spam and "ham" (non-spam) emails. The system's **task (T)** is to flag new spam emails, its **experience (E)** is the training data, and its **performance measure (P)** could be the ratio of correctly classified emails (accuracy).
* **Distinction**: Simply downloading a large amount of data (like Wikipedia) does not mean a computer has "learned" or become smarter in the context of Machine Learning.

---

## 2. Why Use Machine Learning?

Machine Learning is particularly beneficial for:

* **Complex Problems**: Solving problems for which there is **no known algorithmic solution**. For example, speech recognition is too complex for traditional, hardcoded approaches.
* **Replacing Complex Rules**: Replacing long lists of **hand-tuned rules** that are hard to maintain. A ML-based spam filter learns patterns automatically, making it shorter, easier to maintain, and often more accurate than rule-based systems.
* **Adapting to Fluctuating Environments**: Building systems that **adapt to changing data or environments**. For instance, a spam filter can automatically adapt to new spam patterns as they emerge.
* **Helping Humans Learn (Data Mining)**: Gaining insights from large datasets, also known as **data mining**.

---

## 3. Types of Machine Learning Systems

ML systems can be categorised by:

* Supervised vs. Unsupervised Learning
* Online vs. Batch Learning
* Instance-based vs. Model-based Learning

These criteria are not mutually exclusive and can be combined.

### 3.1. Supervised Learning

* **Characteristic**: The **training data is labeled**, meaning it includes the desired solutions (labels or target values) for each instance.
* **Common Tasks**:
    * **Classification**: Predicting a discrete class. The spam filter is a classic example, trained with emails labeled as "spam" or "ham".
    * **Regression**: Predicting a **target numeric value** based on input features (predictors). An example is predicting car prices based on mileage, age, and brand.
        * **Univariate Regression**: Predicting a value based on a single feature (e.g., life satisfaction based on GDP per capita).
        * **Multivariate Regression**: Predicting a value based on multiple features (e.g., housing prices based on population, median income, etc.).
* **Interchangeability**: Some regression algorithms can be used for classification, and vice versa (e.g., Logistic Regression for classification).
* **Important Supervised Learning Algorithms**: k-Nearest Neighbors, Linear Regression, Logistic Regression, Support Vector Machines (SVMs), Decision Trees, Random Forests, and Neural networks.

### 3.2. Unsupervised Learning

* **Characteristic**: The **training data is unlabeled**; the system tries to learn without a "teacher".
* **Common Tasks**:
    * **Clustering**: Grouping similar instances together. Examples include customer segmentation. **Algorithms**: k-Means, Hierarchical Cluster Analysis (HCA), Expectation Maximization.
    * **Visualization and Dimensionality Reduction**: Representing complex, unlabeled data in 2D or 3D while preserving as much structure as possible, helping to understand data organisation and identify patterns.
        * **Dimensionality Reduction**: Simplifying data without losing too much information, often by merging correlated features (feature extraction). It can speed up training and save space. **Algorithms**: Principal Component Analysis (PCA), Kernel PCA, Locally-Linear Embedding (LLE), t-distributed Stochastic Neighbor Embedding (t-SNE).
    * **Anomaly Detection**: Identifying unusual instances (e.g., fraud detection, manufacturing defects, removing outliers). The system is trained on normal instances and identifies deviations.
    * **Association Rule Learning**: Discovering interesting relationships between attributes in large datasets (e.g., items frequently bought together in a supermarket).

### 3.3. Semi-supervised Learning

* **Characteristic**: Deals with **partially labeled data**, typically a large amount of unlabeled data and a small amount of labeled data.
* **Approach**: Most semi-supervised algorithms combine unsupervised and supervised techniques. For example, Deep Belief Networks (DBNs) use unsupervised Restricted Boltzmann Machines (RBMs) for pre-training, followed by supervised fine-tuning.

### 3.4. Reinforcement Learning (RL)

* **Characteristic**: A **learning system (agent)** observes an environment, selects and performs actions, and receives **rewards or penalties** in return. The agent learns to find the best strategy (policy) to maximise total reward over time.
* **Example**: Robots learning to walk, DeepMind's AlphaGo program beating the world champion in Go.
* **Problem Context**: Best suited for problems where a robot needs to learn to walk in various unknown terrains.

### 3.5. Batch Learning vs. Online Learning

* **Batch Learning (Offline Learning)**:
    * **Characteristic**: The system is trained using **all available data at once**.
    * **Process**: Requires significant time and computing resources, typically performed offline. To incorporate new data, the system must be retrained from scratch on the full dataset, then the old system is replaced by the new one.
    * **Automation**: The process can be automated for adaptation to change.
    * **Suitability**: Ideal when data is small enough to fit in memory, there is no continuous data flow, and rapid adaptation is not needed.
    * **Large Data**: For huge datasets, batch learning can be split across multiple servers (e.g., using MapReduce).
* **Online Learning**:
    * **Characteristic**: The system is trained **incrementally**, by feeding data instances sequentially, either individually or in small groups (mini-batches).
    * **Advantages**: Fast and cheap learning steps, allowing the system to adapt to new data on the fly. Good for continuous data streams, autonomous systems with limited resources, or very large datasets (out-of-core learning).
    * **Out-of-core Learning**: Handles datasets too large to fit in main memory by feeding them in mini-batches.

### 3.6. Instance-based Learning vs. Model-based Learning

* **Instance-based Learning**:
    * **Characteristic**: The system **learns examples by heart** and generalises to new cases using a **similarity measure**.
    * **Example**: A spam filter might flag emails very similar to known spam by counting common words.
* **Model-based Learning**:
    * **Characteristic**: The system **builds a model** from examples and uses that model to make predictions.
    * **Process**: Involves:
        1.  **Model Selection**: Choosing a model type (e.g., linear model).
        2.  **Performance Measure**: Defining a **utility function** (measures how good) or a **cost function** (measures how bad) to evaluate the model. For linear regression, Mean Squared Error (MSE) is common, aiming to minimise the distance between predictions and actual values.
        3.  **Training the Model**: An algorithm (e.g., Linear Regression) finds the optimal parameter values that minimise the cost function.
        4.  **Inference**: Applying the trained model to make predictions on new cases, hoping it will generalise well.
    * **Model Parameters**: Values that determine what a model will predict (e.g., $\theta_0$ and $\theta_1$ in a linear model). The learning algorithm finds optimal values for these.

---

## 4. Main Challenges in Machine Learning

* **Insufficient Training Data**: Most ML algorithms need **thousands to millions of examples** to work properly, especially for complex problems like image recognition. More data often matters more than algorithm choice for complex problems.
* **Nonrepresentative Training Data**: Training data must be **representative of new cases** for the model to generalise well. Using unrepresentative data can lead to poor generalisation.
* **Irrelevant Features**: The system learns effectively only if the training data contains **enough relevant features and not too many irrelevant ones**.
    * **Feature Engineering**: The process of creating a good set of features to train on, involving:
        * **Feature Selection**: Choosing the most useful existing features.
        * **Feature Extraction**: Combining existing features to create more useful ones (e.g., dimensionality reduction).
        * **Creating New Features**: Gathering new data.
* **Overfitting the Training Data**: Occurs when the model performs well on the training data but **does not generalise well to new instances**. This happens if the model is too complex relative to the amount and noisiness of data.
    * **Solutions**:
        * Simplify the model: Reduce parameters, attributes, or constrain the model.
        * Gather more training data.
        * Reduce noise in training data: Fix errors, remove outliers.
    * **Regularisation**: Constraining a model to make it simpler and reduce overfitting risk. The amount of regularisation is controlled by a **hyperparameter**.
* **Underfitting the Training Data**: Occurs when the model is too simple to learn the underlying structure of the data, performing poorly on both training and generalisation. This indicates high bias.
    * **Solutions**:
        * Increase model complexity (e.g., add more parameters, reduce regularisation).
        * Provide better features (feature engineering).
        * Reduce constraints on the model.
* **No Free Lunch (NFL) Theorem**: States that if no assumptions are made about the data, **no one model is a priori guaranteed to work better than any other**. In practice, reasonable assumptions are made, and a few suitable models are evaluated.

---

## 5. Testing and Validating

* **Generalisation Error**: The error rate on new, unseen cases.
* **Test Set**: A portion of the data (e.g., 20%) **held out from training** and used to estimate the model's generalisation error before deployment. If training error is low but generalisation error is high, the model is overfitting.
* **Data Snooping Bias**: The risk of optimistically estimating generalisation error by looking at the test set too early, leading to an over-confident but poorly performing system.
* **Validation Set**: A subset of the training data used for **model comparison and hyperparameter tuning**.
* **Cross-Validation**: A common technique to compare models and tune hyperparameters **without needing a separate validation set**. The training set is split into complementary subsets, and models are trained on different combinations and validated on the remaining parts. After selection, the final model is trained on the full training set, and the generalisation error is measured on the test set.