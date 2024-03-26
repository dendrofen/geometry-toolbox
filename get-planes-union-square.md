## getPlanesUnionSquare

Calculates the union square of multiple overlapping planes.

### Description:

This function calculates the union square of multiple planes considering their overlap. It takes any number of plane objects as parameters and iterates over each pair of planes to find the total area covered by both planes while taking their intersection into account.

### Parameters:

- `...planes`: An array of plane objects, where each plane object contains the following properties:
  - `x`: The x-coordinate of the top-left corner of the plane.
  - `y`: The y-coordinate of the top-left corner of the plane.
  - `width`: The width of the plane.
  - `height`: The height of the plane.

### Returns:

- The total union square of the overlapping planes.


### Code:

```javascript
function getPlanesUnionSquare(...planes) {
    let unionArea = 0;

    // Iterate over each pair of planes
    for (let i = 0; i < planes.length; i++) {
        for (let j = i + 1; j < planes.length; j++) {
            const plane1 = planes[i];
            const plane2 = planes[j];

            // Calculate the intersection coordinates
            const minX = Math.max(plane1.x, plane2.x);
            const minY = Math.max(plane1.y, plane2.y);
            const maxX = Math.min(plane1.x + plane1.width, plane2.x + plane2.width);
            const maxY = Math.min(plane1.y + plane1.height, plane2.y + plane2.height);

            // Calculate the intersection area
            const intersectionWidth = Math.max(0, maxX - minX);
            const intersectionHeight = Math.max(0, maxY - minY);
            const intersectionArea = intersectionWidth * intersectionHeight;

            // Calculate the union area
            const area1 = plane1.width * plane1.height;
            const area2 = plane2.width * plane2.height;
            const currentUnionArea = area1 + area2 - intersectionArea;

            // Add the current union area to the total union area
            unionArea += currentUnionArea;
        }
    }

    return unionArea;
}

```

### Example Usage:

```javascript
const plane1 = { x: 0, y: 0, width: 10, height: 10 };
const plane2 = { x: 5, y: 5, width: 10, height: 10 };
const plane3 = { x: 8, y: 8, width: 10, height: 10 };

const unionSquare = getPlanesUnionSquare(plane1, plane2, plane3);
console.log(unionSquare); // Output: Total union square of the overlapping planes
