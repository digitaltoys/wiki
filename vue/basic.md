### radio
```html
<template>
    <div>
        <input type="radio" v-model="radioValues" value="1R">
        <input type="radio" v-model="radioValues" value="2R">
        <input type="radio" v-model="radioValues" value="3R">
        <input type="radio" v-model="radioValues" value="4R">
        {{radioValues}}
    </div>
</template>

<script>
export default {
    data(){
        return{
            radioValues: '',
        }
    }
}
</script>
```

### cookie
```js
import VueCookies from "vue-cookies";
//쿠키를 사용한다.
Vue.use(VueCookies);

//쿠키의 만료일은 7일이다. (글로벌 세팅)
Vue.$cookies.config("7d");
this.$cookies.set("userid", "user1", "7d");
```
