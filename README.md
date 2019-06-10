# random-checker
某サイトのラジオボタンを自動でランダム選択するやつ


## 研究
<a 　　　　href="javascript:javascript%3A(function()%7Bconst%20items%3D%5B...document.querySelectorAll(%22input%5Btype%3D'radio'%5D%22)%5D.reduce((a%2Cc)%3D%3E%7Bconst%20quizId%3Dc.id.split('%3A')%5B0%5D%3Bif(quizId%5B0%5D%20!%3D%3D'q')return%20a%3Bconst%20questionId%3Dc.id.split('%3A')%5B1%5D.split('_')%5B0%5D%3Bconst%20questionAnser%3Dc.id.split('%3A')%5B1%5D.split('_')%5B1%5D%3Bif(!a%5BquizId%5D)a%5BquizId%5D%3D%7B%7D%3Bif(!a%5BquizId%5D%5BquestionId%5D)a%5BquizId%5D%5BquestionId%5D%3D%5B%5D%3Ba%5BquizId%5D%5BquestionId%5D.push(questionAnser)%3Breturn%20a%3B%7D%2C%7B%7D)%3Bconst%20ifServy%3Dfalse%3Bfor(const%20key%20in%20items%5BObject.keys(items)%5B0%5D%5D)%7Bif(ifServy)%7Bif(key%20%3C%3D4)continue%3B%7Delse%7Bif(key%20%3E%3D5%20%26%26%20key%20%3C%3D8)continue%3B%7Dconst%20answers%3Ditems%5BObject.keys(items)%5B0%5D%5D%5Bkey%5D%3Bconst%20answer%3Danswers%5BMath.floor(Math.random()*%20Math.floor(answers.length%20-%201))%5D%3Bconst%20element%3Ddocument.getElementById(%60%24%7BObject.keys(items)%5B0%5D%7D%3A%24%7Bkey%7D_%24%7Banswer%7D%60)%3Belement.checked%3Dtrue%3B%7D%7D)()%3Bvoid(0);">ランダム研究発表</a>

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
