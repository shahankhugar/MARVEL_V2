# Task 21 — Watch & Reflect: Intro to Machine Learning

**Name:** Shashank Hugar
**Program:** UVCE MARVEL AI/ML — Level 1
**Status:** ✅ Completed

---

## What I Understood from the Videos

Before watching these I had a rough idea of what ML was — computers learning stuff. But after going through both videos it actually clicked properly.

The StatQuest video explained it in a way that made sense without going too deep into math. The basic idea is that instead of writing rules for every possible situation, you just give the computer a bunch of examples and it figures out the pattern on its own. That's it. That's machine learning.

---

## The Three Types of ML

**Supervised Learning** is where you give the model data that already has answers. Like if you want to build a spam filter, you show it thousands of emails that are already labeled spam or not spam. It learns from those and then can classify new emails it's never seen. Most real world ML is this type.

**Unsupervised Learning** is different — there are no labels. You just throw data at the model and it finds groupings or patterns on its own. An example would be a company trying to group their customers by behaviour without knowing in advance what groups exist. The model figures that out itself.

**Reinforcement Learning** is the most interesting one to me. The model learns by doing — it tries something, gets a reward if it was good or a penalty if it was bad, and slowly gets better. This is how AlphaGo learned to beat humans at chess. No one programmed it with chess strategies — it just played millions of games and figured it out.

---

## What I Learned from the Data Preparation Video

This one actually surprised me. I assumed the hard part of ML was building the model. Turns out preparing the data before training takes up most of the time — apparently around 80% of a data scientist's work.

Raw data from the real world is messy. There are missing values, duplicate rows, wrong data types, and columns that are completely useless for what you're trying to predict. If you just throw this directly into a model the results will be garbage — literally called "garbage in, garbage out."

So before training you have to:

- **Clean the data** — fix or remove missing values, remove duplicates
- **Pick the right features** — not every column helps. Some are irrelevant and just confuse the model
- **Normalize or standardize** — this was something I actually did in Task 5. The California Housing dataset had features on completely different scales, so we had to normalize them before gradient descent would work properly
- **Split into train and test sets** — usually 80/20. You train on one part and test on the other so you know if the model actually learned something or just memorized the training data

---

## My Reflection

The two videos together made more sense than either one alone. The first tells you what ML is trying to do. The second tells you what you have to do before ML can even start. I think a lot of people skip to the algorithms and ignore the data prep part — but from what I've seen in Task 5, bad data preparation directly hurts your results. A simple model on clean well-prepared data can easily beat a complex model on messy data.

---

*UVCE MARVEL AI/ML Level 1 — Task 21*
