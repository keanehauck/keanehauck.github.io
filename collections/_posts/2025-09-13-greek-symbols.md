---
layout: post
title: How to Write Greek Letters
date: 2025-09-13
summary: Now with a fun rainbow sketchpad.
categories: test
---

![spikedmath](/images/posts/greek-symbols/spikedmath.jpg)

What does every great statistician need the ability to do? If you answered *easily explain complicated theorems* or *derive complex formulae by hand*, you are incorrect. The true answer is that every stats person needs to be able to draw Greek letters on a whiteboard without them looking like scribbly blobs.

This is something I am unsurprisingly bad at. 



<iframe 
  id="rainbowFrame"
  src="/images/posts/greek-symbols/rainbow-draw.html" 
  width="100%" 
  style="border:none; overflow:hidden;" 
  scrolling="no">
</iframe>

<script>
window.addEventListener("message", (ev) => {
  if (ev.data && ev.data.type === "resize-iframe") {
    const iframe = document.getElementById("rainbowFrame");
    if (iframe) iframe.style.height = ev.data.height + "px";
  }
});
</script>


