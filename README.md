# Frontend Mentor - Article preview component solution

This is a solution to the [Article preview component challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/article-preview-component-dYBN_pYFT).
## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
  - [Continued development](#continued-development)
  - [Useful resources](#useful-resources)
- [Author](#author)

## Overview

### The challenge

Users should be able to:

- View the optimal layout for the component depending on their device's screen size
- See the social media share links when they click the share icon

### Screenshot

![](./images/screenshot-desktop.jpg)
![](./images/screenshot-desktop-active.jpg)
![](./images/screenshot-mobile.jpg)
![](./images/screenshot-mobile-active.jpg)


### Links

- Solution URL: [https://github.com/hoangnam-nguyen/article-preview](https://github.com/hoangnam-nguyen/article-preview)
- Live Site URL: [https://hoangnam-nguyen.github.io/article-preview/](https://hoangnam-nguyen.github.io/article-preview/)

## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties
- Flexbox
- Mobile-first workflow
- JavaScript

### What I learned

- To make the tooltip in desktop view always stays at a relative position to the button, while still able to overflow the whole design's border: First put both the tooltip (`.share-window`) and the button (`.share-btn`) in a same div, then set the tooltip's position to be `absolute` relatively to the `main` component, finally make tooltip `overflow: visible`.

```html
<div class="share-img">
  <div class="share-window">
    <p>Share</p>
    <a href="#">
      <img src="images/icon-facebook.svg" alt="facebook icon">
    </a>
    <a href="#">
      <img src="images/icon-twitter.svg" alt="twitter icon">
    </a>
    <a href="#">
      <img src="images/icon-pinterest.svg" alt="pinterest icon">
    </a>
  </div>
  <div class="share-btn">
    <img class="share-icon" src="images/icon-share.svg" alt="share button">
  </div>
</div>
```

```css
main {
  position: relative;
}

.share-window {
  position: absolute;
  overflow: visible;
  left: auto;
  right: -2.9rem;
  bottom: 5.5rem;
  width: 15rem;
  height: 2.5rem;
  border-radius: .5rem;
  padding: 0 2rem;
  transition: 500ms;
    }
```

- To add the arrow to the tooltip

```css
.share-window::after {
    content: "";
    position: absolute;
    top: 100%;
    left: 50%;
    margin-left: -.5rem;
    border-width: .5rem;
    border-style: solid;
    border-color: var(--clr-very-dark) transparent transparent transparent;
}
```

- Toggle classes and images with JavaScript

```js
const shareImg = document.querySelector('.share-img');
const shareWindow = document.querySelector('.share-window');
const shareBtn = document.querySelector('.share-btn');
const shareIcon = document.querySelector('.share-icon');

shareBtn.addEventListener('click', () => {
  shareWindow.classList.toggle('active');
  shareBtn.classList.toggle('transform-share-img');
  if (shareWindow.classList.contains('active')) {
    shareIcon.src = "images/icon-share-active.svg";
  } else {
    shareIcon.src = "images/icon-share.svg";
  }
})
```

### Continued development

I added some hover effects to the share buttons, only to make it look more refined.

### Useful resources

- [How to make tooltip arrow to any direction](https://www.w3schools.com/css/css_tooltip.asp) - This helped me for creating a custom tooltip. I used to do this automatically using D3 visualization, so I find this guide really interesting and will use it going forward.

## Author

- GitHub - [Nguyen Hoang Nam](https://github.com/hoangnam-nguyen)
- Frontend Mentor - [@hoangnam-nguyen](https://www.frontendmentor.io/profile/hoangnam-nguyen)
- CodePen - [@hoangnam-nguyen](https://codepen.io/hoangnam-nguyen)


