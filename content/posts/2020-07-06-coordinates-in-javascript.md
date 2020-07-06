---
template: post
title: Coordinates in Javascript
slug: jscoordinates
draft: false
date: 2020-07-02T09:54:43.906Z
description: >
  Using coordinates in JavaScript for features like drag and drop or figma like
  products.
category: Web
tags:
  - Web
---
To move elements around we should be familiar with coordinates.
Most JavaScript methods deal with one of two coordinate systems:
- Relative to the window – similar to position:fixed, calculated from the window top/left edge.we’ll denote these coordinates as clientX/clientY.
- Relative to the document – similar to position:absolute in the document root, calculated from the document top/left edge.we’ll denote them pageX/pageY.

Drag’n’Drop is a great interface solution. Taking something and dragging and dropping it is a clear and simple way to do many things, from copying and moving documents (as in file managers) to ordering (dropping items into a cart).
But native Drag Events also have limitations. For instance, we can’t prevent dragging from a certain area. Also we can’t make the dragging “horizontal” or “vertical” only. And there are many other drag’n’drop tasks that can’t be done using them. Also, mobile device support for such events is very weak.

**Drag’n’Drop algorithm**

The basic Drag’n’Drop algorithm looks like this:
- On mousedown – prepare the element for moving, if needed (maybe create a clone of it, add a class to it or whatever).
- Then on mousemove move it by changing left/top with position:absolute.
- On mouseup – perform all actions related to finishing the drag’n’drop.

here is an example:
```
ball.onmousedown = function(event) {
  // (1) prepare to moving: make absolute and on top by z-index
  ball.style.position = 'absolute';
  ball.style.zIndex = 1000;

  // move it out of any current parents directly into body
  // to make it positioned relative to the body
  document.body.append(ball);

  // centers the ball at (pageX, pageY) coordinates
  function moveAt(pageX, pageY) {
    ball.style.left = pageX - ball.offsetWidth / 2 + 'px';
    ball.style.top = pageY - ball.offsetHeight / 2 + 'px';
  }

  // move our absolutely positioned ball under the pointer
  moveAt(event.pageX, event.pageY);

  function onMouseMove(event) {
    moveAt(event.pageX, event.pageY);
  }

  // (2) move the ball on mousemove
  document.addEventListener('mousemove', onMouseMove);

  // (3) drop the ball, remove unneeded handlers
  ball.onmouseup = function() {
    document.removeEventListener('mousemove', onMouseMove);
    ball.onmouseup = null;
  };

};
```
