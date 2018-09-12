<template>
    <div id="tablamovil" style="margin-left: -5px;"  >
        <div class="table-responsive-xs " 
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
                        {{e.name}} -  <small id="fech"> {{fecha(e.date)}} {{hora(e.fulldate)}}</small>
 
                        </div>

                      </div>
                             
                             <div class="cabcontenedor">     
                              
                            <div class="cabcuotas">      
                          <div class=" btn1 btns " style="font-size: 10px;">  <small>1</small>
                          <div id="btncuota"> {{e.data[19992].o1}}</div></div>

                           <div class="btnx  btns " style=" font-size: 10px;"> <small>X</small>
                               <div id="btncuota">{{e.data[19992].o2}}</div></div>

                          <div class="btn2  btns " style=" font-size: 10px;"> <small>2</small>
                              <div id="btncuota">{{e.data[19992].o3}} </div></div> 
                           </div>   
                           <!-- <th
                                 scope="row"
                                 v-if="e.data[139992]"
                                 v-for="(cuota,index2) in e.data[139992]"
                                 :key="cuota, index2">
                                               
                                         
                                     
                          <td> <div class=" botn btns btns:hover " style="font-size: 10px;">{{e.data[139992].o1}}</div></td>

                          <td> <div class=" botn btns btns:hover " style=" font-size: 10px;">{{e.data[139992].o2}}</div></td> 

                           <td><div class=" botn btns btns:hover " style=" font-size: 10px;">{{e.data[139992].o3}} </div></td>                                         
                                       
                           </th>                 -->
                                                                         
                                           


                                        <!-- <th><small id="lig">{{e.name}}</small> </th>                                
                                        <th><small id="fech">{{fecha(e.date)}}</small></th>
                                        <th><small id="fech">{{hora(e.fulldate)}}</small></th> -->
                                                                
                                            <!-- <th scope="col" style="word-spacing: 10px; ">UN OV T</th>
                                            <th scope="col" style="word-spacing: 11px; ">1X 12 2X</th>
                                            <th scope="col" style="word-spacing: 5px; ">GG NG</th> -->
                                            <!-- <th scope="col">OTHERS</th> -->

                        </div>  
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


export default {
    
     mounted() {
    axios
      .get("http://91.121.116.131/8abet/admin/api/match")
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
          return moment(e).format('LT');
        //   moment(e).format('LT');   
      },


    //   c:function ( ){
          
    //     this.mostrar = !this.mostrar
    //   },

  }


};
</script>