
<template>
    <div>
    <div class="profileUserA d-flex ">
      <div class="d-flex">
        <img src="../assets/profile2.png" />
        <div class="align-self-center ml-2">
          <h3>{{jsonInfo.user.userB.name}}</h3>
          <span>{{jsonInfo.user.userB.designation}} </span>
        </div>
      </div>
      <div class="align-self-center otherInfo">
        <p>Account Number: {{jsonInfo.user.userB.accno}}</p>
        <p>Currency Status: {{jsonInfo.user.userB.currency}}</p>
      </div>
    </div>
    
    <div class="profileUserInfo tCustomAlign d-flex">
      <div class="text-start ml-2">
        <p>Total Amount </p>
        <span>€{{parseInt(jsonInfo.user.userB.totalBalance)}}(Euro) </span>
      </div>
      <div class="text-end ml-2">
        <p>Transaction Times </p>
        <span>{{jsonInfo.user.transitionInfo.length}}</span>
      </div>
    </div>
    <div>
      <div>
        <div class="bHeader">
              <h4>Transaction History</h4>
              <button class="btn btn-cus" @click="clearAll">Clear All</button>
      </div>
      <div class="cardList">
          <div v-for="(item,index) in jsonInfo.user.transitionInfo" :key="index">
            
            <div class="cardItem">
              <div class="d-flex cardItemHeader">
                <p>From: <span>{{item.from}}</span> </p>
                <p>To: <span>{{item.to}}</span></p>
              </div>
            <div class="d-flex cardItemBody">
              <div>
                <p>Tx Id: <span>{{item.tx}}</span> </p>
                <p><span>{{item.postingDateTime}}</span></p>
              </div>
              <div class="text-end">
                <p>Amount: <span>{{item.amount}} {{jsonInfo.user.userB.currency}}</span></p>
                <p>Charge: <span>{{item.charge}} {{jsonInfo.user.userB.currency}}</span></p>
              </div>
            </div>
            </div>
          </div>
      </div>
      </div>
    </div>
      <!-- comment goes here  <div> </div>-->
    </div>
</template>

<script>
import jsonInfo from '../components/jsonFile.json'
export default {
  name: 'UserB',
  data() {
    // console.log(jsonInfo);
    return {
      jsonInfo,
    } 
  },
  methods: {
  clearAll() {
    window.location.reload();
  }
},
 
}
</script>

<style >
.profileUserInfo{
  background:#4120A2;
  border-radius:10px;
  padding:30px;
  color:#fff;
  justify-content: space-between;
}
.profileUserInfo span{
  font-size: 30px;
  font-weight:600;
}
.profileUserInfo p{
  margin:0;
}
.profileUserA{
  margin:40px 0;
}
.btn-custom{
width:100%;
background:#4120A2!important;
color:#fff!important;
margin-bottom:20px;
}
.profileUserA img{
margin-right:20px;
max-width:100px;
}
.cardList{
  height: 300px;
  overflow-y: scroll;
  scrollbar-color: rebeccapurple green;
  scrollbar-width: thin;
  margin-bottom:50px ;
}
.tCustomAlign{
  text-align: right;
}
.cardItem{
  margin: 15px 20px;
  border-radius: 10px;
  background-color: #eaeaea;
  font-family: "Quicksand";
}
.cardItemHeader{
 
  justify-content: space-between;
  padding: 15px;
  border-radius: 10px 10px 0 0;
  border-bottom: 1px solid #bdbbbb;
}
.cardItemHeader p{
  margin: 0;
}

.cardItemBody{
  color: rgb(33, 32, 32);
  justify-content: space-between;
  padding: 15px;
}
.cardItemBody p{
  margin:0;
}
.cardItem span{
  font-weight: 600;
}
.bHeader{
  justify-content: space-between;
  display: flex;
  font-family: "Quicksand";
  margin-block: 20px;
}
.btn-cus{
  background:#4120A2!important;
  color:#fff!important;
  margin-bottom:20px;
  border: 0;
  font-size: 16px;
  width:30%;
}
</style>

