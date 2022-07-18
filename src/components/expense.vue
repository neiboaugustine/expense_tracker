<template>
  <div class="text-center mt-5 container">
    <h1>Expense Tracker App</h1>

    <!-- input -->
    <form action="submit">
      <div class="d-flex">
        <label for="item"><h3>Name:</h3></label>
        <input
          id="item"
          type="text"
          class="form-control"
          placeholder="what was the expense made on?" v-model="description.name"
        />
      </div>
      <br /><br />
      <div class="d-flex">
        <label for="date"><h3>Date:</h3></label>
        <input id="date" v-model="description.date" type="date" class="form-control" />
        <label for="amount"><h3>Amount:</h3></label>
        <input id="amount" type="text" value="N" v-model="description.amount" class="form-control" />
      </div><br>
      <button @click="addExpense" type="submit" class="btn btn-dark">Add</button>
    </form>

    <table class="table table-bordered mt-5">
        <thead>
        <tr>
          <th scope="col">Name</th>
          <th scope="col">Date</th>
          <th scope="col" class="text-center">Amount</th>
          <th scope="col" class="text-center">Delete</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item,index) in description" :key="index">
          <td><span>{{item.name}}</span></td>
          <td><span>{{item.date}}</span></td>
          <td><span>{{item.amount}}</span></td>
          <td @click="deleteItem"><span id="delete"><i class="fas fa-trash"></i></span></td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "expenseTracker",
  
  data(){
    return{
      item:'',
      date:'',
      amount:'',
      description:[
        {
          name:'notebook',
          date:'16/07/2022',
          amount:'200'
        }
      ]
      
    }
  },
  methods:{
     addExpense(e){
      e.preventDefault()
      if(this.name===0)return;
      if(this.date===0)return;
      if(this.amount===0)return;

      this.description.push({
        name:this.description.name,
        date:this.description.date,
        amount:this.description.amount
      }) 
      this.description.name=''
      this.description.date=''
      this.description.amount=''
  },
  deleteItem(index){
        this.description.splice(index,1)
        this.description.amount=null
      }
  }
 
};
</script>

<style scoped>
.d-flex {
  max-width: 80%;
  margin-left: 10%;
}
.btn{
  width: 100px;
}
#delete{
  cursor: pointer;
}
</style>