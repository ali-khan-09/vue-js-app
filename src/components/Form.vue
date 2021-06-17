<template>
    <div>
        <form class="bg-light m-2 p-4" @submit="addTask">
            <div class="form-group">
        
        <input type="text" name="task" v-model="task"  class="form-control" placeholder="Enter Task Here">
    </div>
     <div class="form-group">
       
        <input type="date" name="date" v-model="date"  class="form-control" placeholder="Enter Date Here">
    </div>
<div class="form-check d-flex flex-column justify-content-start alugn-items-start">
    <input type="checkbox" class="form-check-input" v-model="reminder">
    <label class="form-check-label" for="exampleCheck1">Reminder</label>
  </div>

  <input type="submit" value="Submit" class="btn btn-block btn-dark mt-3">
        </form>
    </div>
</template>

<script>
export default {
    name:"Form",
    data()
    {
        return {
            task:"",
            date:'',
            reminder:false
        }
    }
,
methods:{
    addTask(e)
    {
        e.preventDefault()
        if(this.task=="")
        {
            alert("Enter te task name")
            return;
        }
          if(this.date=="")
        {
            alert("Enter te date ")
            return;
        }

     const task = {
         id:Math.floor(Math.random()*1000),
         text:this.task,
         time:this.date,
         reminder:this.reminder,
     }
    
        this.$emit("addTask",task);
        this.task="";
        this.date=""
        this.reminder=false

    }
}
}
</script>