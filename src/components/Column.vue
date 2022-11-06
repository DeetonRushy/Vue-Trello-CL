<script setup>
import { ref } from 'vue'
import MellowTicket from "@/components/Ticket";
import {Icon} from "@iconify/vue";

const tickets = ref([1])
const title = ref('')

function addNewTicket() {
  const last = tickets.value[tickets.value.length -1]
  tickets.value.push(last + 1)
}

function removeTicket(idx) {
  tickets.value.splice(idx, 1)
}

</script>

<template>
  <div class="column">
    <Icon
        icon="akar-icons:circle-x-fill"
        :inline="true"
        width="10"
        color="white"
        class="ticket-close-icon"
        @click="$emit('column-removed', index)"
    />
    <input v-model="title" placeholder="Title..." class="column-title-input" />
    <MellowTicket v-for="(item, index) in tickets" :key="index" @removed="removeTicket" />
    <button @click="addNewTicket" class="column-button">Add new ticket</button>
  </div>
</template>

<script>
import Ticket from "@/components/Ticket";

export default {
  name: "MellowColumn",
  components: [
    Icon,
    Ticket
  ],
  props: {
    initialTitle: String,
    index: Number
  }
}
</script>

<style scoped>

.column {
  position: relative;
  display: flex;
  flex-direction: column;
  flex-wrap: nowrap;

  width: 300px;
  border: 1px solid black;
  padding: 5px;
  margin: 10px;

  background-color: #2c3e50;
}

.column-button{
  display: flex;
  align-self: center;
}

.column-title-input {
  background-color: inherit;
  color: white;
  border: 0;
}

input {
  padding-bottom: 10px;
  text-align: center;
}

input[class="column-title-input"]:focus {
  outline: none;
}

button {
  background-color: inherit;
  border: 1px black;
  color: white;
  margin: auto;
}

button:hover {
  border: 1px dashed black;
}

</style>