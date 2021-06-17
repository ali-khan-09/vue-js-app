<template>
    <header>
        <h1>{{title}}</h1>
        <Button classes="btn btn-primary" btnText="Add Task" @toggle-form="$emit('toggle-form')"/>
    </header>
</template>

<script>
import Button from "./Button.vue";
export default {
    name:"Header",
    components:{
        Button

    },
    props:{
        title:String,
    }
}
</script>
<style scoped>
header{
    display: flex;
    justify-content: space-between;
    align-content: center;
    margin-bottom: 20px;
    padding: 10px;
 
}
</style>