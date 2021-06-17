<template>
    <div :class="classes" @dblclick="$emit('toggle-reminder',task.id)">
       <div class="title">
            <h3 >{{ task.text }}</h3>
            <i @click="delete1(task.id)"  class="fa fa-trash-o" aria-hidden="true"></i>
       </div>
        <p v-text="task.time"></p>
    </div>
</template>

<script>
export default {
    name:"Task",
    props:{
        task:Object,
    },
    methods:{
        delete1()
        {
            this.$emit("delete-task");
        }
    },
    computed:{
        classes()
        {
            return (this.task.reminder)?" border-green":"";
        }
    }
}
</script>

<style scoped>
div{
    display: flex;
    flex-direction: column;
    justify-content: start;
    margin-bottom: 2vw;
    padding: 1vw 2vw;
    background: #E6E6FA;
    border: 2px solid #fff4;
    text-align: unset;
    align-items: end;
}
.title {
    display: flex;
    justify-content: space-between;
    flex-direction: row;
    width: 100%;
    border: unset;
    padding: 0;
}
.title i{
    color: red;
    cursor: pointer;
}
.border-green
{
    border-left: 5px solid #0275d8;
}
</style>