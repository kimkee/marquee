## MARQUEE

```js
requestAnimationFrame(callback);
```

```html
<div class="marquee">
    <div class="marquee-text" id="marquee-text">반갑습니다! 김선생님! 여기는 JavaScript로 만든 반복되는 애니메이션 효과입니다!</div>
</div>
```

```js
const marqueeText = document.getElementById('marquee-text');
let marqueeWidth = marqueeText.offsetWidth;
let containerWidth = document.querySelector('.marquee').offsetWidth;
let start = containerWidth;
let end = -marqueeWidth;
let current = start;

let lastTime = 0; // 마지막 애니메이션 시간을 추적
const fps = 30; // 초당 프레임 수
const fpsInterval = 1000 / fps; // 프레임 간격

function animateMarquee(timestamp) {
    requestAnimationFrame(animateMarquee);

    // 현재 시간과 마지막 애니메이션 실행 시간의 차이가 fpsInterval보다 작으면 업데이트하지 않음
    if (timestamp - lastTime < fpsInterval) {
    return;
    }
    
    lastTime = timestamp; // 마지막 애니메이션 시간 업데이트

    current -= 2; // 속도 조절 가능
    if (current < end) {
    current = start;
    }
    marqueeText.style.transform = `translateX(${current}px)`;
}

requestAnimationFrame(animateMarquee);
```