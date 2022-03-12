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
