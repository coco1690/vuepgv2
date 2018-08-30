<template>
    <div id="tabla" style="margin-left: -5px;"  >
        <div class="table-responsive-xs " 
            v-for="(idmatches,index) in idmatch" 
            :key="idmatches, index"
            >
            
            <div class="panel-group">
                <div class="panel-default">
                    <div class="center panel-heading">
                        <a class="nav-link active text-white" data-toggle="collapse" :href="'#collapse'+ index">
                        
                            {{idmatches.sportName}} : {{idmatches.name}}   <i class="flecha fa fa-angle-down rotate-icon "></i>
                        </a>
                    </div>
                    <div  :id="'collapse'+ index" class="panel-collapse collapse">
                   <ul class="list-group ">
                                <table class="text-white table-hover">
                                    <!-- <button @click="c">mostar/ocultar</button> -->
                                    <thead >
                                        <tr style=" width: 100%">
                                            <th class="relojcolumn" ><i class=" rlj fa fa-clock-o"></i> </th>
                                            <th id="lig">{{idmatches.sportName}} : {{idmatches.name}}</th>
                                            <th style="word-spacing: 24px;">1 X 2</th>

                                            <!-- <th style="word-spacing: 10px; ">UN OV T</th>
                                            <th style="word-spacing: 11px; ">1X 12 2X</th>
                                            <th style="word-spacing: 5px; ">GG NG</th>
                                            <th >OTHERS</th> -->
                                        </tr>
                                    </thead>
                                 
                     
                       
                        <tbody style=" width: 100%;"
                        v-if="idmatches.matches"
                        v-for="(e,i) in idmatches.matches"
                        :key="e,i">
                                        <tr>
                                        <td >
                                        
                                            <small id="fech">{{fecha(e.date)}}</small>
                                            
                                        </td>
                                        <td>
                                           
                                        <small id="lig">{{e.name}}</small> 
                                        </td>
                                     
                                        <th
                                         v-if="e.data[19992]"
                                           v-for="(cuota,index2) in e.data[19992]"
                                           :key="cuota, index2">
                                        
                                       
                                        
                                           <td> 
                                           
                                               
                                        <div class="row" style="margin-left:-12px">
                                            <div class=" botn btns btns:hover " style="font-size: 10px;">{{e.data[19992].o1}}</div>
                                            <div class=" botn btns btns:hover " style=" font-size: 10px;">{{e.data[19992].o2}} </div>
                                            <div class=" botn btns btns:hover " style=" font-size: 10px;"></div>                                              
                                        </div>
                                            </td>
                                        
                                    
                                       
                                        </th> 
                                        </tr>
                                           <!-- <div v-hide>
                                                   {{index2}}
                                                 </div> -->
                         </tbody>           
                  
                    

                    
                                </table>
                            
                        
                        </ul>
                </div>
                </div>

            </div>


    </div>
 </div>
   
</template>

<script>
import axios from "axios";
import moment from "moment"


export default {
    
     mounted() {
    axios
      .get("http://91.121.116.131/geek/api/list/model/siguiente")
      .then(response => {
        this.idmatch = response.data;
      });
  },

  name: "tabla",

  data() {
    return {

      mostrar:false,
   
      idmatch: [],
      
    };
  },

  methods: {
      fecha:function(d) {
          return moment(d).format("MMM D");                
      },

      hora:function(e) {
          return moment(e).format('h:mm a');
          
      },

    //   c:function ( ){
          
    //     this.mostrar = !this.mostrar
    //   },

  }


};
</script>

