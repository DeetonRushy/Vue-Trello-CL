<script setup>
import { Icon } from '@iconify/vue'
</script>

<template>
  <div class="mellow-banner">
    <Icon icon="mdi:sleep" :inline="true" width="25" color="white" class="banner-logo"/>
    <p class="banner-text">
      {{ msg }}
    </p>
  </div>
</template>

<script>
export default {
  name: 'MellowBanner',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.mellow-banner{
  display: flex;
  background-color: #2c3e50;
  border: thick double #2c3e50;
}

.banner-text {
  color: #fff769;
  font-family: monospace;
  font-size: large;
}

.banner-logo {
  height: inherit;
  width: inherit;
  padding-right: 10px;
}

</style>
