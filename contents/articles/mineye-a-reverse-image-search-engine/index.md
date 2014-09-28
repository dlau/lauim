---
title: Mineye, a reverse image search engine
author: daryl
date: 2014-04-23
template: article.jade
tags: experiments, dev, python
---

Been experimenting a bit with generic object detection and similarity matching using just public libraries, the result can be found here:

[github link](https://github.com/dlau/mineye)

![animation](https://camo.githubusercontent.com/86fffc11c105ef55de202c7db53cec535bb5ee4c/687474703a2f2f692e6375626575706c6f61642e636f6d2f386e566a644f2e676966)

I'll write up a more detailed description soon, but the idea is simple.

- A user uploads an image
- Analyze the image and stick everything into a gigantic matrix. This matrix is just a concatenation of descriptor vectors from our detector. In the project I'm using SURF, but you probably want to use something different, due to patent issues.
- To look up similar images, do a nearest neighbor search on the mega matrix versus the descriptors of the image you are checking against. This "similarity" is calculated using lowe's technique, (match[0].distance < .6*match[1].distance)
    - In practice, this kNN search is pretty slow, so we use [FLANN](http://www.cs.ubc.ca/~mariusm/uploads/FLANN/manual.pdf) to get an approximate nearest neighbor


*hope to revisit this in the future*
