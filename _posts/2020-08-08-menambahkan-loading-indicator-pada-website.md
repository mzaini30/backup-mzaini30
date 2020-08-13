---
layout: post
title: Menambahkan loading indicator pada website
---

`progress.css`

```css
/* Progress Bar */
.progress-loading {
  position: relative;
  height: 4px;
  display: block;
  width: 100%;
  background-color: #acece6;
  border-radius: 2px;
  background-clip: padding-box;
  margin: 0.5rem 0 1rem 0;
  overflow: hidden; 

  position: fixed;
  top: 0;
  left: 0;
  margin-top: 0;
  z-index: 100000;
}
  .progress-loading .indeterminate {
    background-color: #26a69a; }
    .progress-loading .indeterminate:before {
      content: '';
      position: absolute;
      background-color: inherit;
      top: 0;
      left: 0;
      bottom: 0;
      will-change: left, right;
      -webkit-animation: indeterminate 2.1s cubic-bezier(0.65, 0.815, 0.735, 0.395) infinite;
              animation: indeterminate 2.1s cubic-bezier(0.65, 0.815, 0.735, 0.395) infinite; }
    .progress-loading .indeterminate:after {
      content: '';
      position: absolute;
      background-color: inherit;
      top: 0;
      left: 0;
      bottom: 0;
      will-change: left, right;
      -webkit-animation: indeterminate-short 2.1s cubic-bezier(0.165, 0.84, 0.44, 1) infinite;
              animation: indeterminate-short 2.1s cubic-bezier(0.165, 0.84, 0.44, 1) infinite;
      -webkit-animation-delay: 1.15s;
              animation-delay: 1.15s; }

@-webkit-keyframes indeterminate {
  0% {
    left: -35%;
    right: 100%; }
  60% {
    left: 100%;
    right: -90%; }
  100% {
    left: 100%;
    right: -90%; } }
@keyframes indeterminate {
  0% {
    left: -35%;
    right: 100%; }
  60% {
    left: 100%;
    right: -90%; }
  100% {
    left: 100%;
    right: -90%; } }
@-webkit-keyframes indeterminate-short {
  0% {
    left: -200%;
    right: 100%; }
  60% {
    left: 107%;
    right: -8%; }
  100% {
    left: 107%;
    right: -8%; } }
@keyframes indeterminate-short {
  0% {
    left: -200%;
    right: 100%; }
  60% {
    left: 107%;
    right: -8%; }
  100% {
    left: 107%;
    right: -8%; } }

.sembunyi {
    display: none;
   }
```

`progress.js`

```javascript
loading = () => document.querySelector('.progress-loading').classList.remove('sembunyi')
   loading_selesai = () => document.querySelector('.progress-loading').classList.add('sembunyi')
```

Di HTML:

```html
<div class="progress-loading sembunyi">
      <div class="indeterminate"></div>
    </div>
<link rel='stylesheet' href='progress.css'>
<script src='progress.js'></script>
```

Contoh cara menggunakan:

```javascript
loading()
fetch('situs.com').then(x => x.json()).then(data => {
 console.log(data)
 loading_selesai()
})
```
