### vaildation create card number

```javascript
            validatecardnumber: function(cardnumber) {
                //빈칸과 대시 제거
                cardnumber = cardnumber.replace(/[ -]/g,'');

                //카드 번호가 유효한지 검사
                //정규식이 캡처 그룹들 중 하나에 들어있는 숫자를 캡처
                var match = /^(?:(94[0-9]{14})|(4[0-9]{12}(?:[0-9]{3})?)|(5[1-5][0-9]{14})|(6(?:011|5[0-9]{2})[0-9]{12})|(3[47][0-9]{13})|(3(?:0[0-5]|[68][0-9])[0-9]{11})|((?:2131|1800|35[0-9]{3})[0-9]{11}))$/.exec(cardnumber);

                if(match) {

                    //정규식 캡처 그룹과 같은 순서로 카드 종류 나열
                    var types = ['BC', 'Visa', 'MasterCard', 'Discover', 'American Express', 'Diners Club', 'JCB'];

                    //일치되는 캡처 그룹 검색
                    //일치부 배열의 0번째 요소 (전체 일치부중 첫 일치부)를 건너뜀
                    for(var i = 1; i < match.length; i++) {
                        if(match[i]) {
                            //해당 그룹에 대한 카드 종류를 표시
                            return types[i-1];
                        }
                    }

                } else {
                    return '';
                }
            },
```

### 이미지 미리보기
```html
<div class="image-container">
    <img style="width: 500px;" id="preview-image" src="https://dummyimage.com/500x500/ffffff/000000.png&text=preview+image">
    <input style="display: block;" type="file" id="input-image">
</div>
```
```javascript
function readImage(input) {

    // 인풋 태그에 파일이 있는 경우
    if(input.files && input.files[0]) {

        // 이미지 파일인지 검사 (생략)

        // FileReader 인스턴스 생성
        const reader = new FileReader()

        // 이미지가 로드가 된 경우
        reader.onload = e => {
            const previewImage = document.getElementById("preview-image")
            previewImage.src = e.target.result
        }

        // reader가 이미지 읽도록 하기
        reader.readAsDataURL(input.files[0])
    }
}

// input file에 change 이벤트 부여
const inputImage = document.getElementById("input-image")
inputImage.addEventListener("change", e => {
    readImage(e.target)
})
```

### 화면 캡쳐후 저장
```javascript
      function capture() {
        html2canvas(document.querySelector("#capture")).then((canvas) => {
          // document.body.appendChild(canvas);
          var myImage = canvas.toDataURL();
          downloadURI(myImage, "저장이미지이름.png");
        });
      }
      function downloadURI(uri, name) {
        var link = document.createElement("a");
        link.download = name;
        link.href = uri;
        document.body.appendChild(link);
        link.click();
      }
```
```html

```

### query to json
```javastring
   var searchParams = new URLSearchParams(this.$route.hash.slice(1));   // 첫부분에 "#" 제거
   this.query = Object.fromEntries(searchParams);
```

### url에 query 파싱
```js
var qs = getQueryStringObject();
var x = qs.x; // 925641
var y = qs.y; // 1666020
var l = qs.level; // 10
```
```js
function getQueryStringObject() {
    var a = window.location.search.substr(1).split('&');
    if (a == "") return {};
    var b = {};
    for (var i = 0; i < a.length; ++i) {
        var p = a[i].split('=', 2);
        if (p.length == 1)
            b[p[0]] = "";
        else
            b[p[0]] = decodeURIComponent(p[1].replace(/\+/g, " "));
    }
    return b;
}
```

### dynamic form으로 api 호출
```js
        submitForm: function (verb, url, data, target) {
            let form = document.createElement("form");
            form.action = url;
            form.method = verb;
            // form.target = target || "_self";
            if (data) {
                for (let key in data) {
                    let input = document.createElement("textarea");
                    input.name = key;
                    input.value = typeof data[key] === "object" ? JSON.stringify(data[key]) : data[key];
                    form.appendChild(input);
                }
            }
            form.style.display = "none";
            document.body.appendChild(form);
            form.submit();
            document.body.removeChild(form);
        },
```
