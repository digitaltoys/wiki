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
