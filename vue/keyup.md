vue

### keyup
```html
<a @click.stop="doThis"></a>
<form @submit.prevent="onSubmit"></form>
<input @keyup.enter="submit">
<input @keyup.page-down="onPageDown">
<input @keyup.alt.67="clear">
```

.stop  : 클릭 이벤트 전파가 중단  
.prevent  
.capture  
.self  
.once  
.passive  

.enter  
.tab  
.delete (“Delete” 와 “Backspace” 키 모두를 캡처합니다)  
.esc  
.space  
.up  
.down  
.left  
.right  

.ctrl  
.alt  
.shift  
.meta  
