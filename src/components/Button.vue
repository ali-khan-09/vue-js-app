<template>
    <button :class="classes" @click="$emit('toggle-form')">{{btnText}}</button>
</template>

<script>
export default {
    name:"Button",
    props:{
        classes:String,
        btnText:String,
    }
}
</script>