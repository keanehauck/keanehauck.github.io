---
layout: post
title: Test
date: 2026-05-20
summary: Test.
categories: statistics teaching ai
---

A useful skill for any quantitative methodologist is fluency with fundamental math concepts. It is crititally important to have a solid working understanding of differentiation, integration, matrix algebra, probability, and many other methods that are relevant in statistical theory and estimation. Unfortunately, I rarely have the opportunity to hone this skill. When I encounter these concepts in the wild, 99% of the time they are being used within the context of an applied proof in some textbook or paper that has already done the work for me. So, I wanted to help myself by creating a small refresher app which gives introductory to intermediate-level math questions and answers. I used AI tools to curate a list of practice problems, and independently created a framework which would let me embed them in this website. Give it a try below!

<iframe 
  id="rainbowFrame"
  src="/images/posts/greek-letters/rainbow-draw.html" 
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

