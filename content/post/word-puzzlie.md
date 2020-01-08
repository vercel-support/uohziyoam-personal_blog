---
title: "Word Puzzle - 连词达人"
date: 2019-02-05T01:52:44-05:00
draft: false
tags: ["连词达人", "Word Puzzle", "Cocos Creator", "Javascript", "微信小程序"]
categories: ["Projects"]
author: "Yizhou Mao"
comment: true
toc: false
# contentCopyright: '<a href="https://maoyizhou.com" rel="noopener" target="_blank">See origin</a>'
---

---

> Source Code: https://github.com/uohziyoam/WordConnectingGame

### Q: Briefly talk about the game Word Puzzle.

#### A: Randomly generate certain numbers of white squares based on three or four different words. Each word has a common letter shared with other words. The game itself requires the users to fill out the blank areas with the corresponding words.

### Q: What is the gameplay of Word Puzzle?

#### A: ![Local Picture](/img/word_puzzle.jpg "连词达人")

<!-- {{< youtube MqQb1aAtqdo >}} -->

<!-- $$ evidence\_{i}=\sum\_{j}W\_{ij}x\_{j}+b\_{i} $$ -->

### Q: How to set difficulties for each level?

#### A: This game includes different levels. As the higher level the user approached, the puzzle requires users to fill out the longer blank areas; and also, the users may need to come up with more and more unfamiliar words.

### Q: The number of words is limited to three to four for each level?

#### A: True.

### Q: Does the game offer additional features?

#### A: The social property of this game is based on the WeChat (a Chinese social media). In the game, every user has the chance to see the ranks for themselves and their friends. It also records the number of coins they have won. Every time the user finds a word, they are rewarded five coins. Five coins can exchange for a hint for one word in the game.

### Q: Does the game store any data?

#### A: Yes, it does. The game records information for each user, including their avatar, nicknames, gender, and also what ranks they have reached so far. These data are used to give users a chance to compete with each other.

### Q: How to achieve the view of the front end?

#### A: We used an engine called cocos creator. It allows us to render the views we need for the game.

### Q: What is the logic behind the game?

#### A: Two dictionaries are used to store all vocabularies for easy mode and hard mode. We choose 3,000 different words in total.

### Q: How to generate those words?

#### A: Randomly pick one word as the seed. Generate all possible permutations based on the letter this word contains. Store the permutations in an array. Go through every permutation in the array and check if it exists in our dictionary. If it exists, then we push this word into a new array. Repeat this process until we find three to four words so that there are enough words for the level.

### Q: If the words can not be found, how to handle the corner case?

#### A: The number of words needed for each level is limited to 4; thus, it is very unlikely that there are not enough words to share the same character.

```javascript
// smaple code
drawLine: function (startPosition, endPosition, lineArr) {
    lineArr.position = startPosition;
    var dt = startPosition.sub(endPosition);
    var radian = Math.atan2(dt.x, dt.y);
    var rotation = (180 * radian / Math.PI + 90) % 360;
    lineArr.rotation = rotation;
    lineArr.width = startPosition.sub(endPosition).mag();
}
```
