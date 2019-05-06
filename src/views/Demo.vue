<template>
  <div class="about">
    <h1>Instructions</h1>
    <ul>
    	<li>Click on "-" to decrement</li>
	    <li>Click on "+" to increment</li>
	    <li>The value's background will turn red once negative</li>
	</ul>

    <result-circle />
    <result-circle count="3" />
  </div>
</template>


<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import ResultCircle from '@/components/ResultCircle.vue'; // @ is an alias to /src

@Component({
  components: {
    ResultCircle,
  },
})
export default class Demo extends Vue {}
</script>
