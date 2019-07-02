<template>
  <div id="app">
    <vue-time-picker/>
  </div>
</template>
<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import VueTimePicker from './components/vue-time-picker.vue';

@Component({
  components: {
    VueTimePicker,
  },
})
export default class App extends Vue {

}
</script>
<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
