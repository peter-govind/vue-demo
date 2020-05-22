<template>
  <div class="result-circle">
    <span>random number : {{ someComputedProp }}</span>
    <button @click="decrementCount($event)">-</button>
	<strong v-bind:class="{'negative':(countValue < 0)}">{{ countValue }}</strong>
    <button @click="incrementCount($event)">+</button>
  </div>
</template>


<script lang="ts">
import { Component, Prop, /* Watch, */ Vue } from 'vue-property-decorator';

@Component
export default class ResultCircle extends Vue {

  @Prop({default: 9})
  public count!: number;

  private innerCount: number = 0;

  protected mounted() {
    this.innerCount = this.count;
  }

  private decrementCount($event: KeyboardEvent) {
    // this.count = $event.target.value;
    // this.count--;
    this.innerCount--;
  }

  private incrementCount($event: KeyboardEvent) {
    // this.count++;
    this.innerCount++;
  }

  /*
  @Watch('count')
  private onPropertyChanged(value: string, oldValue: string) {
    // Do stuff with the watcher here.
    // console.log('was ' + oldValue + ', now ' + value);
    // console.log(this.count);
  }
  */

  get countValue(): number {
    // return this.count;
    return this.innerCount;
  }

  set countValue(c: number) {
    // this.count = c;
    this.$emit('update:count', c);
  }

  get someComputedProp() {
    return Math.floor(Math.random() * 100);
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.result-circle {
  margin:2em 0 3em 0;
}
.result-circle strong {
  font-size:8em;
  text-shadow: 3px 2px gray;
  vertical-align: middle;
  background-color:#77FF88;
  padding:0.1em 0.15em;
  border-radius:0.2em;
}
.result-circle strong.negative {
  background-color:#FF7788;
}
button {
  margin:0 1em;
  color: #42b983;
  display:inline-block;
}
</style>

