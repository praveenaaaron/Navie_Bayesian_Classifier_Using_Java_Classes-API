

# 📌 Simple Naïve Bayes Classifier (Java)

This project implements a **Naïve Bayes Classifier** in Java using only **core Java libraries** (no external ML libraries).
It works on a **CSV dataset** where the **last column is the class label**.

---

## 🚀 Features

* Pure Java implementation (using `HashMap` for frequency counts).
* Splits dataset into **Training (70%)** and **Testing (30%)**.
* Implements **Laplace smoothing (+1)** to avoid zero probability errors.
* Prints **Accuracy, Precision, and Recall** for each class.

---

## 🛠️ How It Works

### 1. **Training Phase**

* Counts the frequency of each **class label**.
* Counts the frequency of each **feature value given a class**.
* Example: if dataset has feature `1=1.1` with class `A`, it stores this in a nested `HashMap`.

```java
classCounts.put(label, classCounts.getOrDefault(label, 0) + 1);
featureCounts.putIfAbsent(feature, new HashMap<>());
Map<String, Integer> featureLabelCounts = featureCounts.get(feature);
featureLabelCounts.put(label, featureLabelCounts.getOrDefault(label, 0) + 1);
```

---

### 2. **Prediction Phase**

* For each class, compute probability:

$$
P(y|x) \propto P(y) \times \prod P(x_i | y)
$$



### 3. **Evaluation**

* Splits dataset: 70% training, 30% testing.
* Compares predictions with actual labels.
* Computes:

  * **Accuracy** = Correct ÷ Total
  * **Precision** = TP ÷ (TP + FP)
  * **Recall** = TP ÷ (TP + FN)

---

## 📂 Dataset Format (Your `data.csv`)

The dataset has 7 rows with **3 numeric features** and **1 class label**:

```
1,2,3,A
1.1,2.1,3.1,A
1.2,2.2,3.2,B
1.3,2.3,3.3,B
1.4,2.4,3.4,A
1.5,2.5,3.5,A
1.6,2.6,3.6,B
1.7,2.7,3.7,A
```

* Columns `1, 2, 3` are features.
* Column `A` is the **label** (class `A` or `B`).



## 📊 Example Output

```
Accuracy: 50.0%
Class: A
  Precision: 0.50
  Recall: 0.50
Class: B
  Precision: 0.50
  Recall: 0.50


## ▶️ How to Run

1. Place your dataset file as `data.csv`.
2. Compile the program:


javac SimpleNaiveBayes.java


3. Run the program:


java SimpleNaiveBayes



