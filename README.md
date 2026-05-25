# Ex05 Image Carousel
## Date: 22/05/2025

## AIM
To create a Image Carousel using React 

## ALGORITHM
### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.

Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.

The carousel starts with the first image, so initialize currentIndex to 0.

### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.

If currentIndex is at the end of the image list (last image), loop back to the first image using modulo:
currentIndex = (currentIndex + 1) % images.length;

Previous Image: When the "Previous" button is clicked, decrement currentIndex.

If currentIndex is at the beginning (first image), loop back to the last image:
currentIndex = (currentIndex - 1 + images.length) % images.length;

### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.

Using the currentIndex, display the corresponding image from the images list.

### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).

Use setInterval to call the nextImage() function at regular intervals.

Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

## PROGRAM
## App.js
```
import Carousel from "./Carousel";

function App() {
  return (
    <div>
      <Carousel />
    </div>
  );
}

export default App;
```
## Carousel.js
```
import React, { useState, useEffect } from "react";
import "./Carousel.css";

const images = [
  "https://picsum.photos/id/1018/800/400",
  "https://picsum.photos/id/1015/800/400",
  "https://picsum.photos/id/1019/800/400"
];

function Carousel() {
  const [currentIndex, setCurrentIndex] = useState(0);

  const nextImage = () => {
    setCurrentIndex((currentIndex + 1) % images.length);
  };

  const prevImage = () => {
    setCurrentIndex(
      (currentIndex - 1 + images.length) % images.length
    );
  };

  useEffect(() => {
    const interval = setInterval(nextImage, 3000);

    return () => clearInterval(interval);
  });

  return (
    <div className="carousel">
      <button onClick={prevImage}>❮</button>

      <img
        src={images[currentIndex]}
        alt="carousel"
      />

      <button onClick={nextImage}>❯</button>
    </div>
  );
}

export default Carousel;
```
## Carousel.css
```
body {
  margin: 0;
  font-family: Arial;
  background: #111;
}

.carousel {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 80px;
}

img {
  width: 800px;
  height: 400px;
  border-radius: 15px;
}

button {
  font-size: 30px;
  padding: 20px;
  border: none;
  cursor: pointer;
  background: orange;
  color: white;
  border-radius: 50%;
  margin: 20px;
}
```
## OUTPUT
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/dcecc32c-79e6-4f19-b83c-91e36c9fd6a7" />



## RESULT
The program for creating Image Carousel using React is executed successfully.
