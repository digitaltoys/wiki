### 속성 무시하기
```css
        .TableTest
        {}

        .TableTest tr td
        {
            padding:0 5px; background-color:Gray;        
        }

        /*추가 클래스 not = 상속받은 클래스를 무시해라*/
        .Test1:not(.TableTest)
        {
            padding-left:10px;
            background-color:Red;
        }
```

### 한글, 영문, 숫자 폰트 따로 지정하기

자주 사용할 만한 유니코드 범위  

한글 범위:  U+AC00-D7A3  
영어 대문자 범위 :  U+0041-005A  
영어 소문자 범위 :   U+0061-007A  
숫자 범위 : U+0030-0039  
특수 문자: U+0020-002F, U+003A-0040, U+005B-0060, U+007B-007E   
```css
@font-face {
    font-family: 'ChosunCentennial';
    src: url(../fonts/ChosunCentennial/ChosunCentennial.eot);
    src: url(../fonts/ChosunCentennial/ChosunCentennial.eot?#iefix) format('embedded-opentype'),
         url(../fonts/ChosunCentennial/ChosunCentennial.woff) format('woff'),
         url(../fonts/ChosunCentennial/ChosunCentennial.ttf) format('truetype');
         unicode-range: U+AC00-D7A3;
        }

@font-face {
    font-family: 'OpenSans';
    src: url(../fonts/OpenSans/OpenSans-Regular.eot);
    src: url(../fonts/OpenSans/OpenSans-Regular.eot?#iefix) format('embedded-opentype'),
         url(../fonts/OpenSans/OpenSans-Regular.woff) format('woff'),
         url(../fonts/OpenSans/OpenSans-Regular.ttf) format('truetype');
         unicode-range: U+26;
}


body {
    font-size: 35px;
    font-family: 'ChosunCentennial', 'OpenSans';
}

* {
    font-family: inherit;
}
```
