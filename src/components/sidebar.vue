<template>
   <div class="sidebar">
        <!-- <div v-for="idd in id" :key=></div> -->
        <div class="menu"
            v-for="(idpais,id) in deportes" 
            :key="idpais, id">
       

<div class="liid panel-group">
  <div class="panel panel-default">
    <div class="panel-heading ">
        <a class="center2 center2:active nav-link active text-white btn:hover " style=" margin-left: -31px" data-toggle="collapse" :href="'#collapse'+ idpais.name">
             <img class="icon" :src="getImgUrl(id)" v-bind:alt="id">
                &nbsp;&nbsp;&nbsp; {{idpais.name}} <i class="flecha fa fa-angle-down rotate-icon "></i>
        </a>
    </div>

    <div
       v-if="idpais.countries"
       v-for="(paises,index1) in idpais.countries"
       :key="paises,index1"
       >
       
      
       
    <div  :id="'collapse'+ idpais.name " class="panel-collapse collapse">
      <ul class="list-group">
        <li class="active  paisess" style=" list-style: none;">
            <a class="nav-link active text-white" data-toggle="collapse"  :href="'#collapse2'+ idpais.name">
                 <i :class="'ficon-inline f-' + index1">
                 </i>
                  <i class="flecha fa fa-angle-down rotate-icon ">
                 </i> 
                      {{paises.name}}
            </a>
        </li> 
        </ul>
         
    </div>

         <!-- <div
        v-for="(idlig,ind) in idliga" 
        :key="idlig, ind"
            >
               
    <div  :id="'collapse2'+idlig.sportName"  class="panel-collapse collapse" >
      <ul class="list-group">
        <li class="active  paisess" style=" list-style: none;">
            <a class="nav-link active text-white" href=""></a>
        </li> 
        </ul>
        </div>
      
     
    </div> -->
    </div>
  <!-- </div> -->
</div>
        
         </div> 
        </div>

    </div>

</template>

<script>
import axios from "axios"

export default {
  
   
    name:"sidebar",

    data(){
     
        return{
            
            deportes:[],
            idliga:{}
        }
       
    },
     methods: {
    getImgUrl(id) {
    var images = require.context('../assets/', false, /\.png$/)
    return images('./' + id + ".png")
  },

  },

  


    mounted(){
        axios.get('http://91.121.116.131/geek/api/list/model/leftpanel/')
        .then(response =>{
            this.deportes = response.data
           
        })

        axios
      .get("http://91.121.116.131/geek/api/list/model/siguiente")
      .then(response => {
        this.idliga = response.data;
      });
    },
       
   }
   


</script>


