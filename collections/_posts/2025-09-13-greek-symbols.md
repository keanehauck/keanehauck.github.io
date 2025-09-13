---
layout: post
title: How to Write Greek Symbols
date: 2025-09-13
summary: Test
categories: test
---

<canvas id="canvas" width="800" height="600"></canvas>

<script>
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

let drawing = false;
let points = []; // stores all path points

canvas.addEventListener('mousedown', e => {
  drawing = true;
  points.push({x: e.offsetX, y: e.offsetY});
});

canvas.addEventListener('mouseup', () => {
  drawing = false;
  points = []; // reset after each stroke
});

canvas.addEventListener('mouseout', () => {
  drawing = false;
  points = [];
});

canvas.addEventListener('mousemove', e => {
  if (!drawing) return;

  points.push({x: e.offsetX, y: e.offsetY});

  // Draw line segment with gradient
  if (points.length > 1) {
    const p1 = points[points.length - 2];
    const p2 = points[points.length - 1];

    const gradient = ctx.createLinearGradient(p1.x, p1.y, p2.x, p2.y);
    gradient.addColorStop(0, `hsl(${points.length % 360}, 100%, 50%)`);
    gradient.addColorStop(1, `hsl(${(points.length + 1) % 360}, 100%, 50%)`);

    ctx.strokeStyle = gradient;
    ctx.lineWidth = 8;
    ctx.lineCap = 'round';

    ctx.beginPath();
    ctx.moveTo(p1.x, p1.y);
    ctx.lineTo(p2.x, p2.y);
    ctx.stroke();
  }
});
</script>

</body>
</html>
