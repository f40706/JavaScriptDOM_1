# JavaScript DOM應用
{%hackmd BJrTq20hE %}
## Document Object Model(DOM)
瀏覽器一運行，會就形成好幾個節點
且允許JavaScript訪問
利用Document找到所有HTML的節點
Document位於最上方能往下一直搜尋
## 如何使用DOM
以下程式碼主要介紹JavaScript如何讀取與設定
以及使用CSS與HTML的方法
:::info
```javascript=
'use strict';

// 選取JavaScript的class，並使用其方法
//設值與讀值
 console.log(document.querySelector('.message').textContent);
document.querySelector('.number').textContent = 13;
document.querySelector('.score').textContent = 10;

document.querySelector('.guess').value = 23;
console.log(document.querySelector('.guess').value); 

```

:::

:::info
```javascript=
'use strict';
//Math.trunc無條件捨棄
let secretNumber = Math.trunc(Math.random() * 20) + 1;
let score = 20;
let highScore = 0;
//註冊按鍵事件
document.querySelector('.check').addEventListener('click', function () {
  const guess = Number(document.querySelector('.guess').value);
  console.log(guess, typeof guess);
  if (!guess) {
    document.querySelector('.message').textContent = '⛔️ No Number!';
  } else if (guess === secretNumber) {
    document.querySelector('.message').textContent = '🎉 Correct Number!';
    document.querySelector('.number').textContent = secretNumber;
    //讀取CSS Style並變更
    document.querySelector('body').style.backgroundColor = '#60b347';
    document.querySelector('.number').style.width = '30rem';
    if (score > highScore) {
      highScore = score;
      document.querySelector('.highscore').textContent = highScore;
    }
  } else if (guess !== secretNumber) {
    if (score > 1) {
      displayMessage(guess > secretNumber ? '📈 Too high!' : '📉 Too low!');
      score--;
      document.querySelector('.score').textContent = score;
    } else {
      document.querySelector('.score').textContent = 0;
      document.querySelector('.number').textContent = secretNumber;
      displayMessage('💥 You lost the game!');
      document.querySelector('body').style.backgroundColor = '#FF0000';
    }
  }
});

document.querySelector('.again').addEventListener('click', function () {
  initData();
});

function initData() {
  score = 20;
  secretNumber = Math.trunc(Math.random() * 20) + 1;
  displayMessage('Start guessing...');
  document.querySelector('.score').textContent = score;
  document.querySelector('.guess').value = '';
  document.querySelector('.number').textContent = '?';
  document.querySelector('.number').style.width = '15rem';
  document.querySelector('body').style.backgroundColor = '#222';
}

function displayMessage(message) {
  document.querySelector('.message').textContent = message;
}
```
:::

###### tags: `JavaScript`