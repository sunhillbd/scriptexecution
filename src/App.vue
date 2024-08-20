<template>
  <div>
    <h2>Script Execution Order</h2>
    <ul>
      <li v-for="id in order" :key="id">{{ id }}</li>
    </ul>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { VulnerabilityScript, getExecutionOrder } from './vulnerabilityScript';

export default defineComponent({
  data() {
    return {
      order: [] as number[]
    };
  },
  mounted() {
    const script1 = new VulnerabilityScript(1, []);
    const script2 = new VulnerabilityScript(2, [1]);
    const script3 = new VulnerabilityScript(3, [2]);
    const script4 = new VulnerabilityScript(4, [2, 3]);

    const scripts = [script4, script3, script2, script1];
    this.order = getExecutionOrder(scripts);

    console.log(this.order); // Output: [1, 2, 3, 4]
  }
});
</script>

