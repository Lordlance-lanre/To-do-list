<template>
    <div class=container>
        <div class="text">
            <input class="border border-5"  type="text" placeholder="type text here" v-model="task"> 
            <button type="button" class="btn btn-warning" @click="submitTask">Submit</button>
        </div>

        <!----table section----->

        <table class="table mt-5">
          <thead>
             <tr>
                <th scope="col">Task</th>
                <th scope="col">Status</th>
                <th scope="col" class="text-center">edit</th>
                <th scope="col" class="text-center">delete</th>
             </tr>
          </thead>
          <tbody>
             <tr v-for="(task, index) in tasks" :key="index">
                <th scope="col">{{ task.name }}</th>
                <td>{{ task.status }}</td>

                <td>
                  <div class="text-center" @click="addItem(index)">
                   <span class="fa fa-pen"></span>
                </div>
                </td>
               
               <td>
                  <div class="text-center" @click="deleteItem(index)">
                   <span class="fa fa-trash"></span>
                  </div>
                </td>
             </tr>
          </tbody>
        </table>
    </div>
</template>

<script>
export default {   
   data() {
      return {
         task: ' ',
         editTask: null,
         tasks: [
            {name: 'Go to the grocery store', status: 'Done'},
            {name: 'Pick up some new toiletries', status: 'Undone'}
         ]
      }
   },
   methods: {
      submitTask() {
         if(this.task.length === 0) return;

         if(this.editedTask === null){
            this.tasks.push({
               name: this.task,
               status: 'new-item'
            });
         }else {
            this.tasks[this.editedTask].name = this.task;
            this.editedTask = null;
         }

         this.task = ' ';
      },
      deleteItem(index) {
         this.tasks.splice(index, 1);
      },
      addItem(index) {
       this.task = this.tasks[index].name,
       this.editedTask = index 
      }
   }
};
</script>

<style scoped>
.border{
    width: 300px;
}
</style>