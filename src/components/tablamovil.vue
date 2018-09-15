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
            v-for="(e,index1) in idmatches.matches"
            :key="index1"
            :e="e">
            

            <div class="cab-movil">
                <div class="cabezeramovil row">
                    <div class="col-12 lig">
                        {{e.name}}  
                        <div><small id="fech">{{dia(e.date)}} / {{fecha(e.date)}} / {{hora(e.timestamp * 1000)}}</small></div>
                        </div>

                      </div>
               </div>       
        <!-- ==========================================1x2================================================== -->

            <div class="panel-group">
                <div class="panel-default">
                    <div class="center panel-heading">
                        <a class="nav-link active text-white" data-toggle="collapse" :href="'#collapse'+ index1">
                        
                        Ganador del partido
                          
                        </a>
                    </div>
                    <div  :id="'collapse'+ index1" class="panel-collapse collapse">
                   <ul class="list-group ">

                       <div class="cabcontenedor">    
                         
                    <div class="cabcuotas">   
                                 <div class="btn-group btn-group-toggle" data-toggle="buttons">
                        <label class="btn btn-secondary btn1" style=" font-size: 10px;">
                            <small>1</small>
                            <input type="radio" name="options" id="option1" autocomplete="off" checked>
                             <div class="btncuota"> {{e.data[19992]?e.data[19992].o1:""}}</div>
                        </label>

                        <label class="btn btn-secondary btnx" style=" font-size: 10px;">
                             <small>X</small>
                            <input type="radio" name="options" id="option2" autocomplete="off">
                             <div class="btncuota">{{e.data[19992]?e.data[19992].o2:""}}</div>
                        </label>

                        <label class="btn btn-secondary btn2" style=" font-size: 10px;">
                            <small>2</small>
                            <input type="radio" name="options" id="option3" autocomplete="off">
                            <div class="btncuota">{{e.data[19992]?e.data[19992].o3:""}} </div>
                        </label>
                    </div>                         
                           </div>   
                        </div>  
                </ul>
                </div>
                </div>  
                </div>   
                 <!-- ==========================================1x2================================================== -->

            <div class="panel-group">
                <div class="panel-default">
                    <div class="center panel-heading">
                        <a class="nav-link active text-white" data-toggle="collapse" :href="'#collapse'+ index1">
                        
                        Doble Chance
                          
                        </a>
                    </div>
                    <div  :id="'collapse'+ index1" class="panel-collapse collapse">
                   <ul class="list-group ">

                       <div class="cabcontenedor">    
                         
                    <div class="cabcuotas">   
                                 <div class="btn-group btn-group-toggle" data-toggle="buttons">
                        <label class="btn btn-secondary btn1" style=" font-size: 10px;">
                            <small>1X</small>
                            <input type="radio" name="options" id="option1" autocomplete="off" checked>
                             <div class="btncuota"> {{e.data[49992]?e.data[49992].o1:""}}</div>
                        </label>

                        <label class="btn btn-secondary btnx" style=" font-size: 10px;">
                             <small>12</small>
                            <input type="radio" name="options" id="option2" autocomplete="off">
                             <div class="btncuota">{{e.data[49992]?e.data[49992].o2:""}}</div>
                        </label>

                        <label class="btn btn-secondary btn2" style=" font-size: 10px;">
                            <small>2X</small>
                            <input type="radio" name="options" id="option3" autocomplete="off">
                            <div class="btncuota">{{e.data[49992]?e.data[49992].o3:""}} </div>
                        </label>
                    </div>                         
                           </div>   
                        </div>  
                </ul>
                </div>
                </div>  
                </div>   

                <!-- ==========================================GGYNG================================================== -->


            <div class="panel-group">
                <div class="panel-default">
                    <div class="center panel-heading">
                        <a class="nav-link active text-white" data-toggle="collapse" :href="'#collapse'+index1">
                        
                        GOL
                          
                        </a>
                    </div>
                    <div  :id="'collapse'+ index1" class="panel-collapse collapse">
                   <ul class="list-group ">

                       <div class="cabcontenedor">    
                         
                    <div class="cabcuotas">   
                                 <div class="btn-group btn-group-toggle" data-toggle="buttons">
                        <label class="btn btn-secondary btn1" style=" font-size: 10px;">
                            <small>GG</small>
                            <input type="radio" name="options" id="option1" autocomplete="off" checked>
                             <div class="btncuota"> {{e.data[139992]?e.data[139992].o1:""}}</div>
                        </label>

                        <!-- <label class="btn btn-secondary btnx" style=" font-size: 10px;">
                           
                            <input type="radio" name="options" id="option2" autocomplete="off">
                             <div class="btncuota"></div>
                        </label> -->

                        <label class="btn btn-secondary btn2" style=" font-size: 10px;">
                            <small>NG</small>
                            <input type="radio" name="options" id="option3" autocomplete="off">
                            <div class="btncuota">{{e.data[139992]?e.data[139992].o2:""}} </div>
                        </label>
                    </div>                         
                           </div>   
                        </div>  
                </ul>
                </div>
                </div>  
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
    // botonactive:function(e) {
    //     console.log(e);
    //     e.target.classList.add("btnactive1");
       
    // }
     
   

  }


};
</script>