<template>
  <div class="hello">
    <p>hello</p>
  <div>{{this.wheel}}</div>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import * as Winwheel from "Winwheel";

@Options({
  props: {
    msg: String,
  },
})
export default class Wheel extends Vue {
  msg!: string;
  wheel: any;
  data: any;
  option = {
    'numSegments': 4,
    'segments': [
      {'fillStyle' : '#eae56f', 'text' : 'Prize One'},
      {'fillStyle' : '#89f26e', 'text' : 'Prize Two'},
      {'fillStyle' : '#7de6ef', 'text' : 'Prize Three'},
      {'fillStyle' : '#e7706f', 'text' : 'Prize Four'}
    ], //part of wheel
    'animation': {
      'type': 'spinToStop',
      'duration': 5,
      'spins': 8
    }
  };

  mounted() {
    // todo retrieve data in localstorage else []
    this.data = null;

    // init wheel
    this.wheel = new Winwheel(this.option);
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
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
