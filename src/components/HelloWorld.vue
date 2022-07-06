<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  </div>
  <div class="flex">
        <h3>GET METHOD</h3>
        <button 
          class="btn"
          @click="getData()"
        >
          get data from internet
        </button>
        <h4 v-show="value">
        {{showData}}
      </h4>
      </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return {
      value:true,
      showData:""
    };
  },
  methods:{
    async getData(){
      this.value=true;
      this.response=await axios.get(' https://api.roastandbrew.coffee/api/v1/companies')
      if(this.response.status===200){
        this.showData=this.response.data;
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
