<template>

<div class="" style="">
  
            <div class="input-group">
                <div class="input-group-prepend" @click="onClick" style="cursor:pointer">
                  <i :class="iconClass" class=" pr-3 pl-3 input-group-text p-1" :style=" {'color':color,'background':bgColor }"></i></div>
                <input 
                :style=" {'color':color,'background':bgColor }" type="text" class="form-control"
                :placeholder="placeHolder"
                @input="atInput"
                 name="" id="">
                   
                 <div class=" sug bg-light animated fadeIn"  v-if="search.length > startAt " style="min-height:100px">
                     <div class="mt-3" style="padding:10px">
                         <div v-if="Array.isArray(suggests) && suggests.length != 0">
                            <div v-for="(s,index) in suggests" :key="s+index" style="cursor:pointer" 
                            @click="itemClick"
                            >
                             {{s.option}}
                             <small style="float:right;color:gray" class="mt-2">{{s.status}} </small>
                             <p><small style="color:gray">/ {{s.description}}  </small></p>
                             
                             <hr>
                         </div>
                         </div>
                         <div v-else>
                              <i class="fa fa-circle-o-notch fa-spin" style="position:absolute;right:45%;top:35%" v-if="status == 'waiting'" ></i>
                              <div v-else style="text-align:center">
                                  <p>{{notFound}}</p>
                              </div>
                         </div>
                     </div>
                 </div>
                </div>
</div>

</template>
<script>

export default {
data(){
  return{
    search : '',
  }
},
 props: {
   suggests: {
   type: Array,
   default:() =>{return [{
     option:'FirstItem',
     description : 'description 1',
     status:'status1',
   } , {
     option:'SecondItem',
     description : 'description 2',
     status:'status2',
   } , {
     option:'ThirdItem',
     description : 'description 2',
     status:'status3',
   }]} ,
  },
  color: {
   type: String,
   default: 'gray',
  },
     bgColor: {
   type: String,
   default: 'silver',
  },
   startAt: {
   type: Number,
   default: 3,
  },

  placeHolder: {
   type: String,
   default: 'Enter what you want',
  },
   iconClass: {
   type: String,
   default: 'fa fa-search',
  },


block: {
   type: Boolean,
   default: true,
  },
 },

 methods: {
  onClick(event) {
   this.$emit("click", event);
  },
  atInput(event) {
   this.search = event.target.value
   this.$emit("input", event);
  },
  itemClick(event){
    this.$emit("itemClick", event);
  }
 }
};
</script>
<style >
@import './fa/css/font-awesome.min.css';
@import './bootstrap.min.css';
@import 'https://cdnjs.cloudflare.com/ajax/libs/animate.css/3.7.2/animate.min.css';


.sug{
 position: absolute;
 margin-top: 45px;
 width: 100%;
 background:white;
 border-bottom-left-radius: 10px;
 border-bottom-right-radius: 10px;
 border:1px white solid
}



</style>