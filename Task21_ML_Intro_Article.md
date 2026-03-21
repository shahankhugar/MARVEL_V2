# Task 21 — Watch & Reflect: Introduction to Machine Learning

**Name:** Shashank Hugar
**Program:** UVCE MARVEL AI/ML — Level 1
**Status:** ✅ Completed

---

## What is Machine Learning?

Machine Learning is a branch of Artificial Intelligence where a computer learns patterns from data instead of being explicitly programmed with rules. In traditional programming, a developer writes step-by-step instructions for every scenario. In machine learning, you feed the model data and let it figure out the rules itself.

StatQuest's introduction breaks ML down into three fundamental types.

**Supervised Learning** is the most common type. You provide the model with labeled data — inputs paired with correct outputs. The model learns the relationship between them and uses that knowledge to predict outputs for new, unseen inputs. A spam filter is a classic example — trained on thousands of emails labeled spam or not spam, it learns to classify new emails on its own.

**Unsupervised Learning** works with unlabeled data. The model has no correct answers to learn from — instead it finds hidden patterns and natural groupings in the data by itself. Customer segmentation is a common application — grouping customers by purchasing behaviour without being told what groups should exist.

**Reinforcement Learning** is learning through trial and error. The model takes actions, receives rewards for good decisions and penalties for bad ones, and gradually improves its strategy. This is how systems like AlphaGo mastered complex games at a superhuman level.

The common thread across all three is the same — the model finds patterns in data that would take humans far too long to identify manually.

---

## How Data is Prepared for Machine Learning

Understanding what ML is only tells half the story. Before any model can learn, the data it learns from must be carefully prepared. AltexSoft's video on data preparation makes clear that this process — called data preprocessing — accounts for roughly 80% of a data scientist's actual work.

Real-world data is almost never clean. It comes with missing values, duplicates, inconsistent formatting, irrelevant columns, and features on wildly different scales. A model trained on this raw data will produce unreliable results — this is the principle of garbage in, garbage out.

**Data Collection** is the first step — gathering data from databases, APIs, sensors, surveys, or web scraping depending on the problem.

**Data Cleaning** involves handling missing values by either filling them with a sensible default (like the column mean) or removing incomplete rows entirely. Duplicates are removed and data types are corrected.

**Feature Engineering** involves deciding which columns are actually useful for prediction and removing the rest. Sometimes new features are created by combining existing ones — for example, deriving age from a date of birth column.

**Normalization and Standardization** bring all features to the same scale. Without this, a feature with values in the thousands dominates a feature with values between 0 and 1, and the model learns a distorted picture of the data. This was applied directly in Task 5 — the California Housing dataset features were standardized before training the gradient descent model for exactly this reason.

**Train-Test Split** divides the prepared data into a training set and a test set — typically 80% and 20%. The model learns from the training set and is evaluated on the test set, which it has never seen. This measures how well the model generalizes to new data rather than just memorizing what it was trained on.

---

## Reflection

These two videos together form a complete picture of how machine learning actually works in practice. The first explains the concept — what a model is trying to do. The second explains the groundwork — what needs to happen before a model can do anything useful. Neither is complete without the other. A strong algorithm on poorly prepared data produces poor results. Well-prepared data fed into even a simple model can produce surprisingly good results. The foundation of good ML work is good data work.

---

*Written as part of UVCE MARVEL AI/ML Level 1 — Task 21*
