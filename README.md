# random-checker
某サイトのラジオボタンを自動でランダム選択するやつ


## 研究
[ランダム研究](javascript%3a%28%20function%28%29%7b%20const%20items%20%3d%20%5b%2e%2e%2edocument%2equerySelectorAll%28%22input%5btype%3d%27radio%27%5d%22%29%5d%2ereduce%28%28a%2c%20c%29%20%3d%3e%20%7b%20const%20quizId%20%3d%20c%2eid%2esplit%28%27%3a%27%29%5b0%5d%3b%20if%20%28quizId%5b0%5d%20%21%3d%3d%20%27q%27%29%20return%20a%3b%20const%20questionId%20%3d%20c%2eid%2esplit%28%27%3a%27%29%5b1%5d%2esplit%28%27_%27%29%5b0%5d%3b%20const%20questionAnser%20%3d%20c%2eid%2esplit%28%27%3a%27%29%5b1%5d%2esplit%28%27_%27%29%5b1%5d%3b%20if%20%28%21a%5bquizId%5d%29%20a%5bquizId%5d%20%3d%20%7b%7d%3b%20if%20%28%21a%5bquizId%5d%5bquestionId%5d%29%20a%5bquizId%5d%5bquestionId%5d%20%3d%20%5b%5d%3b%20a%5bquizId%5d%5bquestionId%5d%2epush%28questionAnser%29%3b%20return%20a%3b%20%7d%2c%20%7b%7d%29%3b%20const%20ifServy%20%3d%20false%3b%20for%20%28const%20key%20in%20items%5bObject%2ekeys%28items%29%5b0%5d%5d%29%20%7b%20if%20%28ifServy%29%20%7b%20if%20%28key%20%3c%3d%204%29%20continue%3b%20%7d%20else%20%7b%20if%20%28key%20%3e%3d%205%20%26%26%20key%20%3c%3d%208%29%20continue%3b%20%7d%20const%20answers%20%3d%20items%5bObject%2ekeys%28items%29%5b0%5d%5d%5bkey%5d%3b%20const%20answer%20%3d%20answers%5bMath%2efloor%28Math%2erandom%28%29%20%2a%20Math%2efloor%28answers%2elength%20%2d%201%29%29%5d%3b%20const%20element%20%3d%20document%2egetElementById%28%60%24%7bObject%2ekeys%28items%29%5b0%5d%7d%3a%24%7bkey%7d_%24%7banswer%7d%60%29%3b%20element%2echecked%20%3d%20true%3b%20%7d%20%7d%20%29%28%29%3b)
```
javascript:(
function(){
    const items = [...document.querySelectorAll("input[type='radio']")].reduce((a, c) => {
    const quizId = c.id.split(':')[0];
    if (quizId[0] !== 'q') return a;
    const questionId = c.id.split(':')[1].split('_')[0];
    const questionAnser = c.id.split(':')[1].split('_')[1];
    if (!a[quizId]) a[quizId] = {};
    if (!a[quizId][questionId]) a[quizId][questionId] = [];
    a[quizId][questionId].push(questionAnser);
    return a;
    }, {});
    const ifServy = false;
    for (const key in items[Object.keys(items)[0]]) {
        if (ifServy) {
            if (key <= 4) continue;
        } else {
            if (key >= 5 && key <= 8) continue;
        }
        const answers = items[Object.keys(items)[0]][key];
        const answer = answers[Math.floor(Math.random() * Math.floor(answers.length - 1))];
        const element = document.getElementById(`${Object.keys(items)[0]}:${key}_${answer}`);
        element.checked = true;
    }
}
)();
```


## サーベイ

```
javascript:(
function(){
    const items = [...document.querySelectorAll("input[type='radio']")].reduce((a, c) => {
    const quizId = c.id.split(':')[0];
    if (quizId[0] !== 'q') return a;
    const questionId = c.id.split(':')[1].split('_')[0];
    const questionAnser = c.id.split(':')[1].split('_')[1];
    if (!a[quizId]) a[quizId] = {};
    if (!a[quizId][questionId]) a[quizId][questionId] = [];
    a[quizId][questionId].push(questionAnser);
    return a;
    }, {});
    const ifServy = true;
    for (const key in items[Object.keys(items)[0]]) {
        if (ifServy) {
            if (key <= 4) continue;
        } else {
            if (key >= 5 && key <= 8) continue;
        }
        const answers = items[Object.keys(items)[0]][key];
        const answer = answers[Math.floor(Math.random() * Math.floor(answers.length - 1))];
        const element = document.getElementById(`${Object.keys(items)[0]}:${key}_${answer}`);
        element.checked = true;
    }
}
)();
```
