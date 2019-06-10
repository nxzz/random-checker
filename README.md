# random-checker
某サイトのラジオボタンを自動でランダム選択するやつ


## 研究
[ランダム-研究](javascript:( function(\){ const items = [...document.querySelectorAll("input[type='radio']"\)].reduce((a, c\) => { const quizId = c.id.split(':'\)[0]; if (quizId[0] !== 'q'\) return a; const questionId = c.id.split(':'\)[1].split('_'\)[0]; const questionAnser = c.id.split(':'\)[1].split('_'\)[1]; if (!a[quizId]\) a[quizId] = {}; if (!a[quizId][questionId]\) a[quizId][questionId] = []; a[quizId][questionId].push(questionAnser\); return a; }, {}\); const ifServy = false; for (const key in items[Object.keys(items\)[0]]\) { if (ifServy\) { if (key <= 4\) continue; } else { if (key >= 5 && key <= 8\) continue; } const answers = items[Object.keys(items\)[0]][key]; const answer = answers[Math.floor(Math.random(\) * Math.floor(answers.length - 1\)\)]; const element = document.getElementById(`${Object.keys(items\)[0]}:${key}_${answer}`\); element.checked = true; } } \)(\);)
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
