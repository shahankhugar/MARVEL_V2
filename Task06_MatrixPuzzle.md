# Task 06 — The Matrix Puzzle: Decode with NumPy

**Name:** Shashank Hugar
**Program:** UVCE MARVEL AI/ML — Level 1
**Status:** ✅ Completed

---

## What is a Matrix?

A matrix is a grid of numbers arranged in rows and columns. In Python, NumPy arrays are used to represent matrices. What makes this relevant to images is that a grayscale image is literally a 2D matrix — every number in the grid represents the brightness of one pixel, ranging from 0 (black) to 255 (white).

So working with a NumPy matrix and working with image pixel data are the same thing.

---

## What is NumPy?

NumPy (Numerical Python) is a library that makes working with large arrays and matrices fast and simple. Instead of writing loops to process each element, NumPy lets you apply operations to entire arrays in one line.

Key operations used in this task:

`np.reshape()` — changes the shape of an array without changing any of its values. A flat list of 10,000 numbers can become a 100×100 grid.

`array.T` (Transpose) — flips the matrix so rows become columns and columns become rows. Used to correct an image that appears sideways.

`np.flip()` — mirrors the array. Reversing the order of elements along an axis corrects an image that is upside down or back-to-front.

`plt.imshow()` — from Matplotlib, this renders a NumPy array as a visible image.

---

## The Problem

A scrambled NumPy array was provided in a file called `encoded_array.npy`. When loaded, it had the shape `(200, 50)` — meaning 200 rows and 50 columns — with 10,000 total elements. This was clearly not the correct shape for the hidden image.

The task was to apply a series of NumPy operations — guided by clues — to transform this scrambled array into its correct form and reveal the hidden image.

---

## Decoding Process

**Clue 1 — Reshape into a square**

The array had 10,000 elements. 10,000 = 100 × 100, so it was reshaped into a 100×100 matrix.

```python
reshaped = data.reshape(100, 100)
```

**Clue 2 — Data is sideways**

The reshaped matrix was transposed to correct the orientation. Transposing swaps rows and columns — fixing an image that appears rotated 90 degrees.

```python
transposed = reshaped.T
```

**Clue 3 — End is the beginning**

The array was flipped — reversing the order of elements to correct an image that was mirrored or inverted.

```python
flipped = np.flip(transposed)
```

**Visualization**

The final decoded matrix was displayed using Matplotlib:

```python
plt.imshow(flipped, cmap='gray')
plt.title("Decoded Image!")
plt.axis('off')
plt.show()
```

The hidden image was successfully revealed after all three operations.

---

## What Each Operation Actually Did

Reshape took a meaningless (200, 50) grid and turned it into a square that could represent an image. Without this step the data has no visual meaning.

Transpose corrected the orientation — the pixel data was stored sideways, so swapping rows and columns rotated it upright.

Flip reversed the array — the data was stored in reverse order, so flipping it put everything back in the correct position.

Each operation undid one layer of the encoding, like solving a puzzle one step at a time.

---

## Key Takeaways

An image is just a matrix of numbers — understanding this is fundamental to computer vision and image processing in AI/ML. NumPy makes it possible to manipulate these matrices with single-line operations instead of complex loops. Reshape, transpose, and flip are among the most commonly used array operations in data science. Matplotlib's `imshow()` is the bridge between raw numerical data and a visible image.

---

## Notebook

https://github.com/shahankhugar/UVCE-MARVEL-AI-ML-001/blob/main/matrix_puzzle.ipynb
