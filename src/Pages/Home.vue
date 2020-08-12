<template>
  <div>
<label>
  Enter insurance coverage amount:  
</label>
<input v-model="coverAmt"
    
        >
        <label>
            <br>
             <br>
  Enter room rent limit:  
</label>
<input
           v-model="rentLimit"
        
        >
        <label>
             <br>
              <br>
  Enter Hospital  room rent :  
 
</label>
<input
        v-model="actual_rent"
        
        >
          <label>
               <br>
              <br>
  Enter total number of days in hospital:  
 
</label>
<input
          v-model="numOfDays"
        
        >

<br>
        <button v-on:click="CalculateAmt(coverAmt, rentLimit, actual_rent, numOfDays)">Calculate Claim Amount </button>
        <p>Your Claim Amount is :{{ClaimAmt}}</p>
  </div>
</template>

<script>
export default {

    name:"Home",
    data(){
        return { Hidden:false,
        ClaimAmt:0}
       
    },
    methods:
    {
        CalculateAmt(coverAmt, rentLimit, actual_rent, numOfDays){

            var rent=Math.min(rentLimit*coverAmt/100,actual_rent);
            console.log(numOfDays);
            console.log(rent*numOfDays);
            this.ClaimAmt= rent*numOfDays;
          
        }
    }

}
</script>

<style>

</style>