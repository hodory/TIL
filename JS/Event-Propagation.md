```html
<!doctype html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        <title>Document</title>
    </head>
    <body>
        <div id="app">
            <a>
                <img src="https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_272x92dp.png"/>
            </a>
        </div>
    </body>
    <script type="application/javascript">
        document.querySelector('#app a').addEventListener('click', function(){
            alert('Second');
        });
        
        document.querySelector('#app img').addEventListener('click', function(){
            alert('First');
        });
    </script>
</html>
```

위와 같이 이벤트를 설정하면<br/>
가장 안쪽에 있는 태그인 *img*의 이벤트가 실행 된 후, 이 태그를 감싸고 있는 부모 태그인 a 태그의 이벤트가 실행된다

이는 이벤트의 전파가 실행되는것인데,<br/>
아래와 같이 우선 실행되는 DOM인 img 태그에서 이벤트 콜백에서 stopPropagation() 을 호출하면 이벤트 전파가 중단된다.

```javascript
document.querySelector('#app img').addEventListener('click', function(e){
    alert('First');
    e.stopPropagation();
});
```


