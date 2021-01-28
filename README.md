# cssAndSass

- 水平、垂直置中

```
.parent {
    position: relative;
}
```

<br>
```
.child {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}
```
<img src="/center.png" style="height: 120px; margin: 10px 30px;">

- 水平動畫 animation

```
.animaiton {
    ...
  animation-name: animationName;  //要執行的動畫影格名稱
  animation-timing-function: ease-out;
  animation-duration: 3s;

  animation: moveInLeft 1s ease-in-out //animation shortened property
}
```

```
@keyframes animationName {    // 設定動畫影格名稱
    0% {
    opacity: 0;
    transform: translateX(-100px);
    //translateX X軸的動畫方向
    //以X 軸 0 為基準， 動畫從左邊進入，所以起始位置為 X(0)的負值
    }
    ....// 0% 為動畫的起始位置，100%為動畫的結束位置，中間可以設定其實時間點
    100% {
    opacity: 1;
    transform: translate(0);
    }
}
```

ref: [animation property](https://www.w3schools.com/cssref/css3_pr_animation.asp)
ref: [transform property](https://www.w3schools.com/cssref/css3_pr_transform.asp)
