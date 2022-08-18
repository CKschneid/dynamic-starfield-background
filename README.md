# Space Animation (:star: Featured CodePen)

A Pen created on CodePen.io. Original URL: [https://codepen.io/chriskschneider/pen/GgPeOe](https://codepen.io/chriskschneider/pen/GgPeOe).

I built a dynamic background that is meant to stimulate a starfield.

### Here is some of the javascript code I wrote to dynamically create each of the star elements:

```js
function generateRandomPercent(min = 0, max = 100) {
  const randomInteger = Math.floor(Math.random() * (max + 1));
  return `${randomInteger}%`;
}
function generateRadomDelay(interval = 3) {
  const randomInteger = Math.random() * (interval + 1);
  return `${randomInteger}s`;
}

function createStar() {
  const star = document.createElement("div");
  star.classList.add("star");
  star.style.top = generateRandomPercent();
  star.style.left = generateRandomPercent();
  star.style.animationDelay = generateRadomDelay();
  return star;
}

function renderStars(amount = 15) {
  const container = document.getElementById("container");
  const placeholdersArray = Array(amount).fill("star_placeholder");
  const starsArray = placeholdersArray.map((starPlacholder, index) =>
    createStar()
  );
  container.append(...starsArray);
}
```
### Here is some of the styling and animation code written in CSS:
```css
.star {
  background-color: #f0f0f0;
  width: 1.5px;
  height: 1.5px;
  position: absolute;
  border: #f0f0f0 0px solid;
  border-radius: 50%;
  opacity: 0;
  box-shadow: 0px 0px 3px 2px rgba(255, 255, 255, 0.5);
  animation-name: glow;
  animation-duration: 5s;
  animation-iteration-count: infinite;
  animation-timing-function: ease-in-out;
}

@keyframes glow {
  0% {
    opacity: 0;
    transform: scale(1, 1);
  }
  20% {
    opacity: 0.5;
  }
  35% {
    opacity: 1;
  }
  50% {
    transform: scale(2, 2);
  }
  100% {
    transform: scale(1, 1);
  }
}
```
