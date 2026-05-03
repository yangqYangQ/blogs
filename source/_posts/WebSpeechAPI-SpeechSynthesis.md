---
title: 使用 Web Speech API 实现网页语音合成（SpeechSynthesis）
date: 2020-12-17
tags:
  - JavaScript
  - Web API
categories:
  - 技术教程
  - 前端开发
updated: 2026-04-19 14:15:00
description: 本文介绍了如何利用浏览器原生的 SpeechSynthesis API 实现文字转语音功能，并提供了一段适配当前页面语言的自动朗读代码示例。
---
### `SpeechSynthesis`

这是一个实验中的 API,不同浏览器提供的语音可能会不同

```javascript
function speak() {
        const synth = window.speechSynthesis;
        let voices = synth.getVoices().filter(voice => voice.lang.startsWith(document.querySelector('html').lang));
        if (voices.length == 0) return;
        let utterThis = new SpeechSynthesisUtterance(document.querySelector('.content').textContent);
        utterThis.voice = voices[0];
        synth.speak(utterThis);
    }
```
