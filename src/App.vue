

<template>
  <div id="app">
   <div class="l container">

        <div class="row">
            <div class="homelogo col-12 col-sm-12 col-md-12 col-lg-6 justify-content-center">
              
                <img class="col-12 col-sm-11 col-md-auto" src="./assets/logo.png" alt="logo">      
               
            </div>
            <div class="col-12 col-sm-12 col-md-6"> 
              <login/>   
            </div>
        </div>
        <hr>
<nav>
        <div class="row">
            <div class="col-sm-12 col-md-12 col-lg-12">
              <div> 
                <navv/> 
              </div>             
            </div>
        </div>
</nav>

        <div class="row centarpanel">
          
            <div class="col-12 col-sm-12 col-md-2 d-block d-md-none d-inline text-white">
           
            <sidebarmovil/>
             
            </div>
     
            <div class="col-sm-12 col-md-2 col-lg-2 d-none d-md-block text-white">
           
            <sidebar/>
             
            </div>
         
                <carrusel class="col-sm-12 col-md-10 col-lg-10 d-none d-md-block"/>
            <div class="col-sm-12 col-md-10 col-lg-10 offset-md-2">
                <tabla/>
           </div>

             <div ><ticket/></div> 
        </div>

    
<!-- <footer>

        <div class="row">
            <div class="col-6 col-sm-6 col-md-6">footer</div>
            <div class="col-6 col-sm-6 col-md-6">footer</div>
        </div>

</footer> -->

    
    </div>
      <router-view/>
  </div>
</template>

<script>
import Login from "./components/login";
import Navv from "./components/nav";
import Sidebar from "./components/sidebar";
import Sidebarmovil from "./components/sidebarmovil";
import Ticket from "./components/ticket";
import Carrusel from "./components/carrusel";
import Tabla from "./components/tabla";

export default {
  name: 'app',
  data () {
    return {
    
    }
  },
  
  components:{
     Login,
     Navv,
     Sidebar,
     Sidebarmovil,
     Tabla,
     Ticket,
     Carrusel,
  }

}
</script>
 <style>
       
     

        .centarpanel{
          min-height: 30rem;
          max-height: 30rem;

        }
        </style>

