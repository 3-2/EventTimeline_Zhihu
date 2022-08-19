当你在刷知乎时，如果你发现有一个提问显示了时间轴，那么可以用下面的代码来正序显示时间轴。注意要将```fetch```后的链接替换成你要看的时间轴所在提问的链接。

在浏览器开发者工具的控制台中执行以下代码。或在地址栏中输入```javascript:```后粘贴以下代码并执行：

```
fetch("https://www.zhihu.com/question/548977991").then(a=>a.text().then(a=>{document.body.textContent="",JSON.parse(new DOMParser().parseFromString(a,"text/html").getElementById("js-initialData").textContent).initialState.entities.questions[547491278].event.events.reverse().forEach(a=>{document.body.innerHTML+=`<p>${new Date(Number(a.created+"000")).toLocaleString()}</p><a style="color: blue" href="${a.url}">${a.content}</a><br><br>`})}))
```
