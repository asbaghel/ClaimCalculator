<template>
  <div>
  <div v-if="pageno===1" class="page">
    <label>Enter insurance coverage amount:</label>
    <input v-model="coverAmt" />
      <br />
      <br />
      
    <label>
    Enter room rent limit:
    </label>
    <input v-model="rentLimit" />
     <button v-on:click="next()">Next</button>
    </div>
     <div v-if="pageno===2" class="page">
    <label>
      
      Enter Hospital room rent :
    </label>
    <input v-model="actual_rent" />
    <br />
      <br />
    <label>
     Enter total number of days in hospital:
    </label>
    <input v-model="numOfDays" />
     <br />
      <br />
       <button v-on:click="next()">Next</button>
</div>
   
    
     <br />
      <br />
       <div v-if="pageno===3" class="page">
    <p>Your Claim Amount is ₹ <span class="amt">{{ClaimAmt}}</span></p>
  
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  data() {
    return {
      Hidden: false,
      ClaimAmt: 0,
      coverAmt: 0,
      rentLimit: 0,
      actual_rent: 0,
      numOfDays: 0,
      pageno:1
    };
  },
  methods: {
    CalculateAmt() {
      var rent = Math.min(
        (this.rentLimit * this.coverAmt) / 100,
        this.actual_rent
      );
      console.log(this.numOfDays);
      console.log(rent * this.numOfDays);
      this.ClaimAmt = rent * this.numOfDays;
    },
    next()
    {
      this.pageno=this.pageno+1;
      if(this.pageno===3)
      {
        this.CalculateAmt();
      }
    }
  },
};
</script>

<style scoped>

.page
{
  border: 1px black solid;
  background: bisque;
  padding: 10px;
  margin: 100px;
}
.amt{
  color:red ;
  font-size: 30px;
}
label{
  padding: 10px;
  margin: 10px;
 
  justify-content: left;
}
input{
  padding: 10px;
  margin: 10px;
}
button{
  padding: 10px;
}

</style>