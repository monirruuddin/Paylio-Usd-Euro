<template>
  <div>
    <NavbarSection />
    <HeroSection />
    <div class="headerTitle">
      <h3 class="container">P2P Money Management System</h3>
    </div>
    <div class="container bgImage">
      <div class="row">
        <div class="col-md-6">
       <UserA/>
        </div>
        <div class="col-md-6">
        <UserB/>
        </div>
      </div>
    </div>
    <Footer />
  </div>
</template>

<script>
import NavbarSection from './components/NavbarSection'
import UserA from './components/UserA'
import UserB from './components/UserB'
import Footer from './components/Footer'
import HeroSection from './components/HeroSection'


export default {
  name: 'App',
  listdata: Array,
  components: {
   NavbarSection,
   UserA,
   UserB,
   Footer,
   HeroSection,
  }
}

</script>

<style>
.headerTitle{
  color:#FFFFFF;
  background:#4e2ab8;
  padding:30px 0;
  font-size:10px;
}
.headerTitle h3{
  font-size:22px;
  font-family: 'Quicksand', sans-serif;
}
/* width */
::-webkit-scrollbar {
  width: 10px;
}

/* Track */
::-webkit-scrollbar-track {
  background: #dfdede; 
  border-radius: 10px;
}
 
/* Handle */
::-webkit-scrollbar-thumb {
  background: #4f2eb3; 
  border-radius: 10px;
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: #6855a3; 
}

</style>
