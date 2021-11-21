<template>
  <div>
      <h1>Dynamic Component latest</h1>

      <b-button @click="tab='comp1'" class="m-2" variant="primary">Comp1</b-button>
      <b-button @click="tab='comp2'" class="m-2" variant="primary">Comp2 </b-button>
      <b-button @click="tab='Comp3'" class="m-2" variant="primary">Comp3</b-button>
      <component :is="tab"/>
  </div>
</template>

<script>
import Comp1 from './Comp1';
import Comp2 from './Comp2';
import Comp3 from './Comp3';
export default {
    name:'DynamicComp',
    
    components:{
        Comp1,
        Comp2,
        Comp3,
    },
    
    data(){
        return{
            tab:"Comp1",
        }
    },

}
</script>

<style>

</style>