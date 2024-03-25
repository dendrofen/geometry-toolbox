## areVectorsSameLength

### Description

This function compares the lengths of two vectors. Given two vectors defined by their starting and ending points `(x1, y1)` and `(x2, y2)`, it calculates the lengths of both vectors using the Euclidean distance formula. Then, it compares the lengths and returns a string indicating whether the lengths are equal or which vector is shorter.

### Parameters

- `vector1`: An object representing the first vector, with properties `x1`, `y1`, `x2`, and `y2` representing the coordinates of its starting and ending points.
- `vector2`: An object representing the second vector, with properties `x1`, `y1`, `x2`, and `y2` representing the coordinates of its starting and ending points.

### Returns

Returns "true" if the vectors are equal.

### Code

```javascript
export function areVectorsSameLength(vector1, vector2) {
    // Calculate the lengths of the vectors
    const length1 = Math.sqrt((vector1.x2 - vector1.x1) ** 2 + (vector1.y2 - vector1.y1) ** 2);
    const length2 = Math.sqrt((vector2.x2 - vector2.x1) ** 2 + (vector2.y2 - vector2.y1) ** 2);

    // Compare the lengths
    if (Math.abs(length1 - length2) < Number.EPSILON) {
        return true;
    }

    return false;
}
