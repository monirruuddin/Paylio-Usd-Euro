<template>
   
    <div>
    <div class="profileUserA d-flex">
      <div class="d-flex">
        <img src="../assets/profile.png" />
        <div class="align-self-center ml-2">
          <h3> {{jsonInfo.user.userA.name}}</h3>
          <span>{{jsonInfo.user.userA.designation}}</span>
        </div>
      </div>
      <div class="align-self-center otherInfo">
        <p>Account Number: {{jsonInfo.user.userA.accno}}</p>
        <p>Currency Status: {{jsonInfo.user.userA.currency}}</p>
      </div>
    </div>
    <div class="profileUserInfo d-flex">
      <div class="ml-2">
        <p>Total Amount </p>
        <span>${{jsonInfo.user.userA.totalBalance}}(Usd)</span>
      </div>
      <div class="text-end ml-2">
        <p>Transaction Times </p>
        <span> {{jsonInfo.user.transitionInfo.length}}</span>
      </div>
    </div>
    <button @click="isActive= !isActive" class="btn-custom btn">  {{isActive ? "Want to Send Money" : "I don't want Send Money"}}</button>
    <transition name="bounce">
      <div v-if="isActive">If You Want to send money,just Click there</div>
      <div v-else>
          <form @submit.prevent="send">
            <div class="mb-3">
              <input type="number" class="form-control" v-model="formInfo.number" placeholder="Enter Amount" >
            </div>
            <div class="mb-3">
              <input type="text" class="form-control" v-model="formInfo.accountnumber" placeholder="Account Number">
            </div>
            <div class="mb-3">
              <input type="password" class="form-control" v-model="formInfo.password" placeholder="Pin">
            </div>
            <button type="submit" @click="submitreset" class="btn btn-custom">Send Money</button>
          </form>
      </div>
    </transition>
    <div v-for="(item, index) in listOfT" :key="index">
        <h2 >{{jsonInfo.user.userA.totaltranfser += item.amount}}</h2>
      </div>
    </div>
    

</template>
<script>
import jsonInfo from '../components/jsonFile.json'
export default {
  name: 'UserA',
  data() {
   
    return {
      jsonInfo,
      isActive: true,
      currentTimeAndDate: '',
      formInfo: {
              number:"",
              accountnumber:"",
              password:"",
      },
      formInfoCopy: {
              number:"",
              accountnumber:"",
              password:"",
      }
    } 
    
  },
  methods: {
    send(){
      if(this.formInfo.number != "" && this.formInfo.number <= this.jsonInfo.user.userA.totalBalance && this.formInfo.number > 0 ){
        if(this.formInfo.accountnumber != "" && this.formInfo.accountnumber == this.jsonInfo.user.userB.accno){
          if(this.formInfo.password != "" && this.formInfo.password == this.jsonInfo.user.userA.pin){
           
            // Find out and add the charge option
            let chargeCondition = this.formInfo.number >= 2000 ? 20 : 0;
            let chargeAdd= (0.94*100*(parseInt(chargeCondition).toFixed(2)))/100;
            
            // Decreasing amount when he transferred money
            this.jsonInfo.user.userA.totalBalance -= this.formInfo.number;
            let dd= this.formInfo.number
            // Store and converted the total balance from dollar into Euro
            this.jsonInfo.user.userB.totalBalance += (0.94*100*(parseInt(dd).toFixed(2)))/100+chargeAdd;
            // Generated random tx number for tracking transaction
            let randomTxID= "Paylio" + Math.floor(Math.random() * (100000 - 55 + 1)) * 59;
           // Created oject for storing data

           let ts = {
            from: this.jsonInfo.user.userA.accno,
            to  : this.jsonInfo.user.userB.accno,
            amount  : (0.94*100*parseInt(this.formInfo.number).toFixed(2))/100,
            tx: randomTxID,
            charge: chargeAdd,
            postingDateTime: this.currentTimeAndDate,
           }

          // storing data
           this.jsonInfo.user.transitionInfo.push(ts);
           this.jsonInfo.user.userA.totaltranfser += this.jsonInfo.user.transitionInfo.amount
          
           // reset the form
          this.resetFormFields();

        }else{
        alert("Pin Number Does Not Match");
      }
        }else{
          alert("Account Number is not Valid");
      }
      }else{
        alert("The Number of Amount is not Valid");
      }
    },
    resetFormFields() {
          this.formInfo.number="";
          this.formInfo.accountnumber="";
          this.formInfo.password="";
          
          // after submiting form the form is alive
          // this.isActive = true;
    },
    updateTimeAndDate() {
      // Get the current time and date
      const currentTime = new Date()

      // Set the timezone to Bangladesh Standard Time (GMT+06:00)
      currentTime.setTime(currentTime.getTime() + (currentTime.getTimezoneOffset() * 60000) + (3600000 * 6))

      // Format the date and time as desired
      const options = {
        year: 'numeric',
        month: 'long',
        day: 'numeric',
        hour: 'numeric',
        minute: 'numeric',
        second: 'numeric',
        hour12: false,
        timeZone: 'Asia/Dhaka'
      }
      this.currentTimeAndDate = currentTime.toLocaleString('en-US', options)
    }
  
  },
  mounted() {
    this.updateTimeAndDate()
    setInterval(() => {
      this.updateTimeAndDate()
    }, 1000)
  }
}
</script>

<style >
.profileUserInfo{
  background:#4120A2;
  border-radius:10px;
  padding:30px;
  color:#fff;
  justify-content: space-between;
  margin:40px 0;
  font-family: "Quicksand";
}
.profileUserInfo span{
  font-size: 30px;
  font-weight:600;
}
.profileUserInfo p{
  margin:0;
}
.profileUserA{
  margin:20px 0;
  justify-content: space-between;
  background: #4120a210;
  padding: 30px;
  border-radius: 20px;
  box-shadow: 0 8px 80px 0 rgb(21 21 49 / 5%);
}

.profileUserA span{
  margin:40px 0;
  justify-content: space-between;
  font-weight:500;
}
.profileUserA h3{
  margin:0;
  font-weight: 700;
  font-family: "Quicksand";
  font-size: 20px;
}
.btn-custom{
width:100%;
background:#4120A2!important;
color:#fff!important;
margin-bottom:20px;
border: 0;
}
.profileUserA img{
margin-right:20px;
max-width:100px;
}
.profileUserA span{
  font-size: 14px;
  color:rgb(54, 53, 53);
  font-family: "Quicksand";
}
.bounce-enter-active {
  animation: bounce-in 0.5s;
}
.bounce-leave-active {
  animation: bounce-in 0.5s reverse;
}
@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.25);
  }
  100% {
    transform: scale(1);
  }
}
.otherInfo{
  font-weight: 600;
  text-align: right;
  font-family: "Quicksand";
}
.otherInfo p{
  margin: 0;
  font-size:13px;
  color:#3c3a3a;
  font-family: "Quicksand";
}
</style>
