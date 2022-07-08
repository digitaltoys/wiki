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

### 차량번호판 체크 정규식
```js
this.carNumber = this.carNumber.replace(/^(\d{2,3}[가-힣]{1}\d{4})([\s\S]*)$/, "$1");

// 입력중 오류 검사
let liveCheck = /^\d{2,3}[가나다라마바사아자거너더러머버서어저고노도로모보소오조구누두루무부수우주배허하호국합육해공]{1}\d{1,4}$|\d{2,3}[가나다라마바사아자거너더러머버서어저고노도로모보소오조구누두루무부수우주배허하호국합육해공]{1}$|^\d{1,3}$/.exec(this.carNumber);
// 입력후 오류 검사
let match = /^(\d{2,3}[가나다라마바사아자거너더러머버서어저고노도로모보소오조구누두루무부수우주배허하호국합육해공]{1}\d{4})$/.exec(this.carNumber);
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

### 일시 배열을 moment로 변환
```js
            arr2moment: function (arr) {
                let arr2 = arr.slice(0,6);
                arr2[1]--;
                return this.$moment(arr2)
            },
```
### 몇초전, 몇분전, 몇일전, 몇주전 구하기
```js
            setTimePass: function (regdtm) {
                // let moment=require('moment')
                // console.log('moment', moment())
                let strToDate = regdtm[0] + "/" + regdtm[1] + "/" + regdtm[2] + " " + regdtm[3] + ":" + regdtm[4] + ":" + regdtm[5];
                let date = this.$moment(strToDate, "YYYY/MM/DD HH:mm:ss");
                // let date = this.$moment(strToDate).format("YYYY/MM/DD HH:mm:ss");
                let current = this.$moment();
                let diffTimes = {
                    year: current.diff(date, "years"),
                    month: current.diff(date, "months"),
                    week: current.diff(date, "weeks"),
                    day: current.diff(date, "days"),
                    hour: current.diff(date, "hours"),
                    minute: current.diff(date, "minutes"),
                    second: current.diff(date, "seconds"),
                };
                if (diffTimes.year > 0) return diffTimes.year + "년 전";
                if (diffTimes.month > 0) return diffTimes.month + "달 전";
                if (diffTimes.week > 0) return diffTimes.week + "주 전";
                if (diffTimes.day > 0) return diffTimes.day + "일 전";
                if (diffTimes.hour > 0) return diffTimes.hour + "시간 전";
                if (diffTimes.minute > 0) return diffTimes.minute + "분 전";
                if (diffTimes.second > 0) return diffTimes.second + "초 전";
                if (diffTimes.second == 0) return "방금 전";
            },
```

### 하위 객체에 값 쓰기
```js
// optWrite(a, 'b.c.e', 2) 
let optWrite = (obj, str, val) => {
    chain = str.split('.');
    let key = chain.shift();
    if (!key) return;

    (chain?.length > 0)? obj[key] = obj[key] || {}: obj[key] = val;// obj[key] = chain.shift();
    console.log(chain?.length, key, JSON.stringify(obj))
    optWrite(obj[key], chain.join('.'), val);
}
```

### axios 에서 params에 '[]' 인식 오류
```js
        const options = {
            method: "GET",
            // url: "/tmap/pois",
            url:"https://apis.openapi.sk.com/tmap/pois",
            params: data.params,
            paramsSerializer: function (params) {
                return qs.stringify(params, {arrayFormat: 'brackets'})
            },
            data: {},
        };
```

### input tag에 키보드 타입설정하기

https://developer.mozilla.org/ko/docs/Web/HTML/Global_attributes/inputmode
**none** - 가상 키보드를 사용하지 않습니다. 페이지가 자체 키보드나 입력 컨트롤을 구현할 때 사용합니다.  
**text (기본값)** - 사용자의 현재 로케일에 맞는 표준 키보드를 제공합니다.  
**decimal** - 사용자의 로케일에 맞는 소숫점(보통 , 또는 .)을 제공하는 숫자형 키보드를 제공합니다. 장치에 따라 음의 부호(-)는 제공할 수도, 제공하지 않을 수도 있습니다.  
**numeric** - 숫자형 키보드를 제공합니다. 소숫점은 없으며, 음의 부호는 제공할 수도, 제공하지 않을 수도 있습니다.  
**tel** - 전화번호 키보드를 제공합니다. 숫자 0~9, 별표(*), 해시(샵, #) 키를 포함합니다. 일반적인 경우, 반드시 전화번호를 필요로 하는 입력 칸에는 <input type="tel"> (en-US)을 사용해야 합니다.  
**search** - 검색 입력 칸에 최적화한 가상 키보드를 제공합니다. 예를 들면, 엔터/제출 키가 "검색" 아이콘이나 레이블을 가질 수 있습니다. 일반적인 경우, 반드시 검색 질의를 필요로 하는 입력 칸에는 <input type="search"> (en-US)를 사용해야 합니다.  
**email** - 이메일 입력에 최적화한 가상 키보드를 제공합니다. 보통 @ 키 등을 제공합니다. 일반적인 경우, 반드시 이메일을 필요로 하는 입력 칸에는 <input type="email"> (en-US)을 사용해야 합니다.  
**url** - 보통 / 키를 누르기 편한 곳에 배치하며, 세션 히스토리 접근 기능 등을 추가하기도 합니다. 일반적인 경우, 반드시 URL을 필요로 하는 입력 칸에는 inputmode 대신 <input type="url"> (en-US)을 사용해야 합니다.  

```html
<input type="text" pattern="[0-9]*" inputmode="numeric" />
```

### 브라우저 테그 영역을 파일로 캡쳐하여 저장하기
```html
<a id="target" style="display: none"></a>

html2canvas(e.target.parentElement).then(function(canvas) {
  var el = document.getElementById("target");
  el.href = canvas.toDataURL("image/jpeg");
  el.download = '파일명.jpg';
  el.click();
});
```
출처: https://sub0709.tistory.com/48 [쓸데없는 코딩하기:티스토리]

```android
    private void convertBase64StringToFileAndStoreIt(String base64PDf) throws IOException {
        final int notificationId = 1;
        String currentDateTime = DateFormat.getDateTimeInstance().format(new Date());
        String newTime = currentDateTime.replaceFirst(", ","_").replaceAll(" ","_").replaceAll(":","-");
        Log.d("fileMimeType ====> ",fileMimeType);
        MimeTypeMap mimeTypeMap = MimeTypeMap.getSingleton();
        String extension = mimeTypeMap.getExtensionFromMimeType(fileMimeType);
        final File dwldsPath = new File(Environment.getExternalStoragePublicDirectory(
                Environment.DIRECTORY_DOWNLOADS) + "/" + newTime + "_." + extension);
        String regex = "^data:" + fileMimeType + ";base64,";
        byte[] pdfAsBytes = Base64.decode(base64PDf.replaceFirst(regex, ""), 0);
        try {
            FileOutputStream os = new FileOutputStream(dwldsPath);
            os.write(pdfAsBytes);
            os.flush();
            os.close();
        } catch (Exception e) {
            Toast.makeText(context, "FAILED TO DOWNLOAD THE FILE!", Toast.LENGTH_SHORT).show();
            e.printStackTrace();
        }
        if (dwldsPath.exists()) {
            Intent intent = new Intent();
            intent.setAction(android.content.Intent.ACTION_VIEW);
            Uri apkURI = FileProvider.getUriForFile(context,context.getApplicationContext().getPackageName() + ".provider", dwldsPath);
            intent.setDataAndType(apkURI, MimeTypeMap.getSingleton().getMimeTypeFromExtension(extension));
            intent.addFlags(Intent.FLAG_GRANT_READ_URI_PERMISSION);
            PendingIntent pendingIntent = PendingIntent.getActivity(context,1, intent, PendingIntent.FLAG_CANCEL_CURRENT);
            String CHANNEL_ID = "MYCHANNEL";
            final NotificationManager notificationManager = (NotificationManager) context.getSystemService(Context.NOTIFICATION_SERVICE);
            NotificationChannel notificationChannel= new NotificationChannel(CHANNEL_ID,"name", NotificationManager.IMPORTANCE_LOW);
            Notification notification = new Notification.Builder(context,CHANNEL_ID)
                    .setContentText("You have got something new!")
                    .setContentTitle("File downloaded")
                    .setContentIntent(pendingIntent)
                    .setChannelId(CHANNEL_ID)
                    .setSmallIcon(android.R.drawable.stat_sys_download_done)
                    .build();
            if (notificationManager != null) {
                notificationManager.createNotificationChannel(notificationChannel);
                notificationManager.notify(notificationId, notification);
            }
        }
        Toast.makeText(context, "FILE DOWNLOADED!", Toast.LENGTH_SHORT).show();
    }
```
https://stackoverflow.com/questions/72181133/how-to-download-blob-url-in-webview

### 클로저(closer)를 우회하는 방법
```js
test = function () {
  for (i=0; i < 3; i++) {
    (function(x) {
      setTimeout(function() {
        console.log(x);
      }, 1000*x);
    })(i);
  }
}
```
