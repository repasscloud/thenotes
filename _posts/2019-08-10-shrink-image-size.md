---
title: Shrink Image Size
author: danijeljw-rpc
date: 2019-08-10 00:00:00 +1000
categories: [Images, Tools]
tags: [images, sips, cli, mogrify]
math: true
mermaid: true
image:
  path: /assets/image/2019/08/10/dall-e-cat-sitting-in-a-hamburger-single-colour-background-pixel-art.jpeg
  alt: Cat sitting in a hamburger single colour background pixel art by Dall-E
---

Shrinking an image with `sips` or `mogrify` using terminal:

```sh
sips -z 512 512 input.jpg --out output.jpg
```

Reduce the resolution of an image to 50% of original:

```sh
mogrify -resize 50% input.jpg
```

Change the format of an image:

```sh
sips -s format jpeg input.png --out output.jpeg
```

**Source:** [https://zaiste.net/posts/command-line-resizing-images/](https://zaiste.net/posts/command-line-resizing-images/)