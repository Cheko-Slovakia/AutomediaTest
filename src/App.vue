<template>
  <div id="app">
    <NumberInput
    v-for="NumberInputs in NumberInputArray"
    v-bind:key="NumberInputs.id"
    v-bind:val="NumberInputs.val"
    v-on:update-value="setValNumberInput"
    ></NumberInput>

    <div>
      <button v-on:click="addNumberInput" class = "calculate-button" >
      {{total}}
      </button>
    </div>

  </div>
</template>

<script>
import NumberInput from './components/NumberInput.vue'

export default {
  name: 'App',
  components: {
    NumberInput
  },
  data: function() {
    return {
     NumberInputArray: [
       {id: 1, val: 10 },
       {id: 2, val: 20},
       {id: 3, val: 25},
       {id: 4, val: 25},
       {id: 5, val: 20}
     ]
    };
  },
  computed: {
    total: function (){
      var sum = 0
      for(var i = 0; i<this.NumberInputArray.length; i++){
        sum += this.NumberInputArray[i].val
      }
      return sum
    }
  },
  methods: {
    setValNumberInput: function (id, newVal){
      if(newVal != "" ){
        this.NumberInputArray[id-1].val = parseInt(newVal)
      } else {
        this.NumberInputArray[id-1].val = 0;
      }
    },
    addNumberInput: function (){
      console.log('new: %s', this.NumberInputArray.length-1)
      this.NumberInputArray.push({id: this.NumberInputArray.length+1,
                                  val: this.getRandomNumber()})
    },
    getRandomNumber: function (){
      return Math.floor(Math.random()*(10-1+1)+1)
    }
  }
}
</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}


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

button.calculate-button{
  width: 358px;
  height: 36px;
  text-align: center;
  margin: 5px;

}
</style>
