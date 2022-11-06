<script setup>
// create a view for columns, tickets etc..

import { ref } from 'vue'
import Column from "@/components/Column";

/* Pretty much hacked my way around state, not sure why.
*
* All states are managed within each component. (other than index)
*
* Don't even ask how I landed on an array of number that literally represent nothing.
* */

const items = ref([1])

const addItem = () => {
  let next = items.value[items.value.length - 1];
  if (next === undefined || next < 0){
    next = 1
    items.value.push(next)
    return
  }
  items.value.push(next + 1)
}

const removeItem = (index) => {
  if (index < 0 || index > items.value.length){
    return
  }
  items.value.splice(index, 1)
}

</script>

<template>
  <div class="home">
    <div v-if="items.length === 0" class="home-disclaimer">
      <p>Add something, or else..</p>
      <br/>
    </div>
    <Column v-for="(item, index) in items" :key="index" :index="index" @column-removed="removeItem(index)" />
    <div class="home-add">
      <button @click="addItem" class="home-add">New</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "HomeView"
}
</script>

<style scoped>

.home {
  position: relative;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}

.home-add {
  padding: 5px;
  margin: 2px;
}

.home-disclaimer {
  margin: auto;
  display: block;
  white-space: nowrap;
}

</style>