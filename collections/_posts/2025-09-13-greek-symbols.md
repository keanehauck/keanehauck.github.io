---
layout: post
title: How to Write Greek Symbols
date: 2025-09-13
summary: Test
categories: test
---

<script>
    const canvas = document.getElementById("canvas");
    const ctx = canvas.getContext("2d");

    const x1 = 50, y1 = 50, x2 = 450, y2 = 50;

    // Create gradient along the line
    const gradient = ctx.createLinearGradient(x1, y1, x2, y2);
    gradient.addColorStop(0, "red");
    gradient.addColorStop(0.17, "orange");
    gradient.addColorStop(0.33, "yellow");
    gradient.addColorStop(0.5, "green");
    gradient.addColorStop(0.67, "blue");
    gradient.addColorStop(0.83, "indigo");
    gradient.addColorStop(1, "violet");

    ctx.strokeStyle = gradient;
    ctx.lineWidth = 10;
    ctx.beginPath();
    ctx.moveTo(x1, y1);
    ctx.lineTo(x2, y2);
    ctx.stroke();
</script>