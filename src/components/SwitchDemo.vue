<template>
<div>
    <z-switch v-model:value="flag"/>
</div>
</template>

<script lang="ts">
import Switch from '../lib/switch.vue';
import {ref,reactive} from "vue";


export default {
    setup(){
      const flag = ref(true);
      const handleChange = () => {
          console.log(111111)
          flag.value = !flag.value;
      }
      return {
          flag,
          handleChange
      }
    },
    components: {
        'zSwitch': Switch
    }
}
</script>
