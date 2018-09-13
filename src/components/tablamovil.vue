<template>
    <div id="tablamovil" style="margin-left: -5px;"  >
        <div 
            v-for="(idmatches,index, value) in idmatch" 
            :key="idmatches, index, value"
            >
            
            <div class="panel-group">
                <div class="panel-default">
                    <div class="center panel-heading">
                        <a class="nav-link active text-white" data-toggle="collapse" :href="'#collapse'+ value">
                        
                          {{idmatches.name}}   <i class="flecha fa fa-angle-down rotate-icon "></i>
                        </a>
                    </div>
                    <div  :id="'collapse'+value" class="panel-collapse collapse">
                   <ul class="list-group ">

            <div class="container"
           
            v-if="idmatches.matches"
            v-for="(e,i) in idmatches.matches"
            :key="e,i">
                <div id="cabezeramovil row">
                    <div class="col-12" id="lig">
                        {{e.name}} -  <small id="fech">{{dia(e.date)}} / {{fecha(e.date)}} / {{hora(e.timestamp * 1000)}}</small>
 
                        </div>

                      </div>
                      
      

            <div class="panel-group">
                <div class="panel-default">
                    <div class="center panel-heading">
                        <a class="nav-link active text-white" data-toggle="collapse" :href="'#collapse'+ i">
                        
                        Ganador del partido
                          
                        </a>
                    </div>
                    <div  :id="'collapse'+ i" class="panel-collapse collapse">
                   <ul class="list-group ">

                       <div class="cabcontenedor">     
                              
                            <div class="cabcuotas">      
                          <div  @click="botonactive" v-bind:class="[isActive ? activeClass : errorClass]" style="font-size: 10px;">  <small>1</small>
                          <div id="btncuota"> {{e.data[19992].o1}}</div></div>

                           <div class="btnx  btns " style=" font-size: 10px;"> <small>X</small>
                               <div id="btncuota">{{e.data[19992].o2}}</div></div>

                          <div @click="botonactive" v-bind:class="[isActive ? activeClass2 : stopClass2]" style=" font-size: 10px;"> <small>2</small>
                              <div id="btncuota">{{e.data[19992].o3}} </div></div> 
                           </div>   
                        </div>  
      
        
         
    

                </ul>
                </div>
                </div>  
                </div>   

               
                <div class="cabcontenedor">  
                    <div class="cabcuotas">
                      
                          
                     
          
                          <div class=" btn1 btns " style="font-size: 10px;">  <small>GG</small>
                          <div id="btncuota"> {{e.data[19992].o1}}</div></div>

                           <div class="btnx  btns  " style=" font-size: 10px;"> <small></small>
                               <div id="btncuota"></div></div>

                          <div class="btn2  btns " style=" font-size: 10px;"> <small>NG</small>
                              <div id="btncuota"> </div>{{e.data[19992].o2}}</div>  
                    
                    
                    </div>
                    </div>   

                                                                         
                                           


                                        <!-- <th><small id="lig">{{e.name}}</small> </th>                                
                                        <th><small id="fech">{{fecha(e.date)}}</small></th>
                                        <th><small id="fech">{{hora(e.fulldate)}}</small></th> -->
                                                                
                                            <!-- <th scope="col" style="word-spacing: 10px; ">UN OV T</th>
                                            <th scope="col" style="word-spacing: 11px; ">1X 12 2X</th>
                                            <th scope="col" style="word-spacing: 5px; ">GG NG</th> -->
                                            <!-- <th scope="col">OTHERS</th> -->

                        
                            </div>
                        
                        </ul>
                </div>
                </div>

            </div>


    </div>
 </div>
   
</template>

<script>
import axios from "axios";
import moment from "moment";

// import moment from "moment-timezone";

moment.locale('es');
export default {
    
     mounted() {
    axios
      .get("http://91.121.116.131/8abet/admin/api/match")
      .then(response => {
        this.idmatch = response.data;
      });
  },

  name: "tablamovil",

  data() {
    return {

    //   mostrar:false,
       isActive: true,
       activeClass:'btn1 btns',
       errorClass:'btnactive1 btns',
       activeClass2:'btn2 btns',
       stopClass2:'btnactive2 btns',

       idmatch: [],
      
    };
  },

  
  methods: {
      fecha:function(d) {
          return moment(d).format("MMM D");                
      },

      hora:function(e) {
         
          return moment(e).format('LT')
        //   moment(e).format('LT');   
      },
      dia:function(e) {
          
          return moment(e).format('dddd')
        //   moment(e).format('LT');   
      },
      hoy:function(e) {
          return moment().startOf('').fromNow();
        //   moment(e).format('LT');   
      },
    botonactive:function() {
        this.isActive =!this.isActive 
        
    }
     
    //   c:function ( ){
          
    //     this.mostrar = !this.mostrar
    //   },

  }


};
</script>