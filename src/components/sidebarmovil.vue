<template>
   <div class="sidebarmovil">
        <!-- <div v-for="idd in id" :key=></div> -->
        <div class="menumovil" 
        v-for="(idsports,id) in idsport" 
        :key="idsports, id"
        
        
        >
       <!-- <div class="row">
            <div class="liid d-inline col-12 col-sm-12"> {{id}}</div>
        </div> -->

    
               <div class="limovil"><a class="nav-link active text-white" href="#" >
                  <!-- {{id}} -->
    
                    <img class="icon" :src="getImgUrl(id)" v-bind:alt="id">
                       {{idsports.name}}
                   </a></div>
        
          
        </div>

    </div>

</template>

<script>
import axios from "axios";


export default {
  
   
    name:"sidebarmovil",

    data(){

        return{
        
            idsport:[]
        }
       
    },

  methods: {
    getImgUrl(id) {
    var images = require.context('../assets/', false, /\.png$/)
    return images('./' + id + ".png")
  }
  },

    mounted(){
        axios.get('http://kingdeportes.com/geek/api/list/model/leftpanel/')
        .then(response =>{
            this.idsport = response.data
           
        })
    },
       
   }
   


</script>