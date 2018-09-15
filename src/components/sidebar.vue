<template>
   <div class="sidebar">
        <!-- <div v-for="idd in id" :key=></div> -->
        <div class="menu"
            v-for="(idpais,id) in deportes" 
            :id="idpais"
            :key="id">
       

<div class="liid panel-group">
  <div class="panel panel-default">
    <div class="cont-deporte panel-heading ">
        <a class="center2 center2:active nav-link active text-white btn:hover " style=" margin-left: -31px" data-toggle="collapse" :href="'#collapse'+ idpais.name">
            
             <div>
                <img class="icon" :src="getImgUrl(id)" v-bind:alt="id">
                <div class="name-sport">
                 {{idpais.name}}
                 <i class="flecha fa fa-angle-down rotate-icon ">
                     </i>
                </div>
            </div>
        </a>
    </div>

    <div
       v-if="idpais.countries"
       v-for="(paises,index) in idpais.countries"
       :key="index"
       :paises="paises"
       >
    
      
       
    <div  :id="'collapse'+ idpais.name " class="panel-collapse collapse">
      <ul class="list-group">
        <li class="active  paisess" style=" list-style: none;">
            <a class="nav-link active text-white" data-toggle="collapse"  :href="'#collapse2'+ index">
                 <i :class="'ficon-inline f-' + index">
                 </i>
                  <i class="flecha fa fa-angle-down rotate-icon ">
                 </i> 
                      {{paises.name}}
            </a>
        </li> 
        </ul>
         
    </div>

         <div
         v-if="paises.leagues"
       v-for="(liga,index1) in paises.leagues"
       :key="index1"
        :liga="liga"   >
               
    <div  :id="'collapse2'+index"  class="panel-collapse collapse" >
      <ul class="list-group">
        <li class="active  paisess" style=" list-style: none;">
            <a class="nav-link active text-white">
                 {{liga.name}}
            </a>
           
        </li> 
        </ul>
        </div>
      
     
    </div>
    </div>
  </div>
</div>
        
         </div> 
        </div>

    <!-- </div> -->

</template>

<script>
import axios from "axios"

export default {
  
   
    name:"sidebar",

    data(){
     
        return{
            
            deportes:[],
            index:{}
        }
       
    },
     methods: {
    getImgUrl(id) {
    var images = require.context('../assets/', false, /\.png$/)
    return images('./' + id + ".png")
  },

  },

  


    mounted(){
        axios.get('http://91.121.116.131/8abet/admin/api/menu')
        .then(response =>{
            this.deportes = response.data
           
        })

    //     axios
    //   .get("http://91.121.116.131/gecko/api/match")
    //   .then(response => {
    //     this.index = response.data;
    //   });
    },
       
   }
   


</script>


