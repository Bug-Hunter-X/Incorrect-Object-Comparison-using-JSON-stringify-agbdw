# Incorrect Object Comparison in TypeScript

This repository demonstrates a common but subtle bug in TypeScript related to object comparison. The `compareObjects` function uses `JSON.stringify` to compare two objects.  This approach has several limitations and can lead to unexpected results.

**Issues:**

* **Property Order:** `JSON.stringify` does not guarantee consistent property order, so objects with the same properties but different order will be considered unequal.
* **Circular References:**  `JSON.stringify` throws an error when encountering circular references.
* **NaN values:** NaN values are not comparable using `JSON.stringify`.
* **Functions and other non-serializable data:** `JSON.stringify` will exclude functions, Dates, etc.

**Solution:**

The provided solution uses a recursive deep comparison function that addresses these limitations.