---
title: 【數位設計與製造】作品集
date: 2025-12-29 08:00:00 +0800
author: Sean
categories: [ 修課心得 ]
tags: [ NYCU, 修課心得 ]
summary: 隨堂練習成果，利用 Fusion360 繪製 3D 模型以熟悉軟體操作，並於期末完成個人專案設計，包含建模與 3D 列印。
---
<script type="module" src="https://ajax.googleapis.com/ajax/libs/model-viewer/3.3.0/model-viewer.min.js"></script>
<style>
  model-viewer {
    width: 100%;
    height: 400px;
    background-color: #303030;
  }
  #error {
    background-color: #ffffffdd;
    border-radius: 16px;
    padding: 16px;
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate3d(-50%, -50%, 0);
    transition: opacity 0.3s;
  }
  #error.hide {
    opacity: 0;
    visibility: hidden;
    transition: visibility 2s, opacity 1s 1s;
  }
  .slider {
    width: 100%;
    text-align: center;
    overflow: hidden;
    position: absolute;
    padding: 0 20px;
    bottom: 16px;
  }
  .slides {
    display: flex;
    overflow-x: auto;
    scroll-snap-type: x mandatory;
    scroll-behavior: smooth;
    -webkit-overflow-scrolling: touch;
  }
  .slide {
    scroll-snap-align: start;
    flex-shrink: 0;
    width: 100px;
    height: 100px;
    background-size: contain;
    background-repeat: no-repeat;
    background-position: center;
    background-color: #fff;
    margin-right: 10px;
    border-radius: 10px;
    border: none;
    display: flex;
    position: relative;
    overflow: hidden;
  }
  .slide.selected {
    border: 2px solid #4285f4;
  }
  .slide:focus {
    outline: none;
  }
  .slide:focus-visible {
    outline: 1px solid #4285f4;
  }
  .label-text {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    background: rgba(0, 0, 0, 0.3);
    color: white;
    font-size: 12px;
    padding: 2px 0;
    text-align: center;
    pointer-events: none;
  }
  .slide.selected .label-text {
    background: rgba(116, 178, 243, 0.5);
  }
  .model-label {
    position: absolute;
    top: 15px;
    right: 15px;
    background: rgba(0, 0, 0, 0.6);
    color: white;
    padding: 8px 15px;
    border-radius: 5px;
    font-family: sans-serif;
    font-size: 14px;
    pointer-events: none;
    z-index: 10;
  }
</style>

### 0910 - Andriod 娃娃

<model-viewer src="/assets/glb/0910 - Android.glb" 
              camera-controls 
              auto-rotate>
</model-viewer>

- 繪製草圖

### 0917 - 翼龍

<model-viewer src="/assets/glb/0917 - 翼龍.glb" 
              camera-controls 
              auto-rotate>
</model-viewer>

- 匯入草圖
- 拉伸（Extrude） - 製作實體
- 管道（Pipe） - 製作卡榫

### 0924 - 精油瓶

<model-viewer src="/assets/glb/0924 - 精油瓶.glb" 
              camera-controls 
              auto-rotate>
</model-viewer>

- 旋轉（Revolve）
- 抽殼（Shell）
- 螺旋（Coil） - 螺紋與瓶蓋製作
- 截面分析（Section Analysis）
- 偏移平面（Offset Plane）

### 0924 - 兔子

<model-viewer src="/assets/glb/0924 - 兔子.glb" 
              camera-controls 
              auto-rotate>
</model-viewer>

- 掃掠（Sweep）- 將輪廓沿著指定曲線延伸
- 球型關節製作

### 1001 - 小雞花瓶

<model-viewer src="/assets/glb/1001 - 小雞花瓶.glb" 
              camera-controls 
              auto-rotate>
</model-viewer>

- 放樣（Loft）

### 1015 - AirPods 保護殼（渲染）

<model-viewer src="/assets/glb/1015 - AirPods 保護殼（渲染）.glb" 
              camera-controls 
              auto-rotate>
</model-viewer>

- 自由造型
- 渲染

### 期末專案

<model-viewer src="/assets/glb/final.glb" 
              poster="/assets/img/post/parametric-design/final.png" 
              shadow-intensity="1" 
              camera-controls 
              touch-action="pan-y"
              class="final"
              style="height: 500px;">
  <div id="model-label" class="model-label">產品外觀</div>

  <div class="slider">
    <div class="slides">
      <button class="slide selected"
              onclick="switchSrc(this, 'final', '產品外觀')"
              style="background-image: url('/assets/img/post/parametric-design/final.png');">
        <span class="label-text">外觀</span>
      </button>
      <button class="slide"
              onclick="switchSrc(this, 'final_open', '展開圖（手機架型態）')"
              style="background-image: url('/assets/img/post/parametric-design/final_open.png');">
        <span class="label-text">展開</span>
      </button>
      <button class="slide"
              onclick="switchSrc(this, 'v1', '第一版 - 自製瓶蓋')"
              style="background-image: url('/assets/img/post/parametric-design/v1.png');">
        <span class="label-text">第一版</span>
      </button>
    </div>
  </div>
</model-viewer>

<div style="position: relative; width: 100%; height: 0; padding-top: 56.2500%;
 padding-bottom: 0; box-shadow: 0 2px 8px 0 rgba(63,69,81,0.16); margin-top: 1.6em; margin-bottom: 0.9em; overflow: hidden;
 border-radius: 8px; will-change: transform;">
  <iframe loading="lazy" style="position: absolute; width: 100%; height: 100%; top: 0; left: 0; border: none; padding: 0;margin: 0;"
    src="https://www.canva.com/design/DAG3FUJmpyY/uq-jndVu6igfJNfd48UFwQ/view?embed" allowfullscreen="allowfullscreen" allow="fullscreen">
  </iframe>
</div>

![](/assets/img/post/parametric-design/poster.png) 

<script>
  const finalModelViewer = document.querySelector("model-viewer.final");
  const label = document.querySelector("#model-label");
  window.switchSrc = (element, name, labelText) => {
    const base = "/assets/glb/" + name;
    finalModelViewer.src = base + ".glb";
    finalModelViewer.poster = base.replace("glb", "img/post/parametric-design") + ".png";
    label.textContent = labelText;
    const slides = document.querySelectorAll(".slide");
    slides.forEach((element) => {element.classList.remove("selected");});
    element.classList.add("selected");
  };
</script>