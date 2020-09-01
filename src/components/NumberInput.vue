<template>
  <div class="number-input">
    <input v-model="updatedVal" type="number" v-on:input="$emit('update-value', theKey, $event.target.value)">
  </div>
</template>

<script>
export default {
  name: 'NumberInput',
  props: {
    val: Number
  },
  computed :{
    updatedVal: {
      get() {
        return this.val
      },
      set(input) {
        return input
      }
    }
  },
  data: function () {
    return {
      theKey: this.$vnode.key
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
