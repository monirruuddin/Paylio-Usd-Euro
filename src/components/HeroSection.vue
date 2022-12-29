<template>
  <div class="banner">
    <div class="container paddingY">
      <div class="row">
        <div class="col-md-6 col-sm-12 align-self-center order-md-1 order-sm-2 orderMaintainContent">
          <div class="bannerContet">
            <h4>Happy Converting! Convert Your Money From Usd To Euro</h4>
            <p>Excepteur sint occaecat cupidatat non proident sunt in culpa qui officia deserunt mollit.</p>
          </div> 
        </div>
        <div class="col-md-6 col-sm-12 order-md-2 order-sm-1 orderMaintainImg">
          <div  class="bannerImage">
            <img src="../../src/assets/vector.png" alt="">
          </div>
         
        </div>
     
      </div>
     
    </div>

    
  </div>
</template>

<script>
export default {
  name: 'HeroSection',
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style >
.banner{
  color: #fff;
  font-family: "Quicksand";
  background: rgb(42,23,99);
  background: linear-gradient(90deg, rgba(42,23,99,1) 0%, rgba(89,41,230,1) 100%);
}
.bannerContet h4{
  font-size:48px;
  font-weight: 700;
}
.bannerContet p{
  font-size: 16px;

}
.paddingY{
  padding: 60px 0;
}
.orderMaintainContent{
  order: 1;
}
.orderMaintainImg{
  order: 2
}
.bannerImage img{
    max-width: 350px;
    
}
.bannerImage {
    
    text-align: center;
  }

@media(max-width:575px) {
  .bannerImage img{
    max-width: 250px;
  }
  .orderMaintainContent{
  order: 2;
  }
  .orderMaintainImg{
    order: 1
  }
  .bannerContet{
    text-align: center;
    margin: 0 40px;
    margin-top: 30px;
  }
  .bannerContet h4{
  font-size:30px;
  font-weight: 700;
  }
  .bannerContet p{
    font-size: 14px;
    margin-top: 10px;

  }
}

@media(min-width:576px) and (max-width:767px) {
  .bannerImage img{
    max-width: 350px;
  }
  .bannerContet{
    text-align: center;
    margin: 0 40px;
    margin-top: 30px;
  }
  .bannerContet h4{
  font-size:35px;
  
  }
  .bannerContet p{
    font-size: 14px;
    margin-top: 10px;

  }
}
@media(min-width:768px) and (max-width:991px) {
  .bannerImage img{
    max-width: 400px;
  }
  .bannerContet h4{
  font-size:40px;
  
  }
}
@media(min-width:992px) and (max-width:1199px) {
  .bannerImage img{
    max-width: 400px;
  }
}

/* @media(min-width:1200px) and (max-width 1400px) {} */
</style>
