---
template: post
title: Debouncing
slug: debouncing
draft: false
date: 2020-05-02T11:45:21.736Z
description: Debouncing in JavaScript. Improving the browser performance.
category: Web
tags:
  - Web
---
Now we all are searching for things all the time, in and outside the Internet. If you like most of us have searched for something in the search box in websites, chances are you have been debounced. Debouncing is a method the limit the number of network calls made to the API. Network calls can be expensive. Moreover, the unnecessary API calls can also cause undue load on our system. 

Here is an example of how you can use debouncing:
```
// Debouncing in Javascript
let counter = 0;
const getData = () => {
  // calls an API and gets Data
  console.log("Fetching Data ..", counter++);
}

const debounce = function (fn, d) {
  let timer;
  return function () {
    let context = this,
      args = arguments;
    clearTimeout(timer);
    timer = setTimeout(() => {
      getData.apply(context, arguments);
    }, d);
  }
}

const betterFunction = debounce(getData, 300);
```
