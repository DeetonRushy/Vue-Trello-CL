<script setup>
import { ref, defineEmits } from 'vue'
import { Icon } from "@iconify/vue";

defineEmits([
    'removed'
])

const ticketName = ref('')
const ticketContents = ref('')

// dont think this needs to be ref
const ContentsOpen = ref(false)

const now = new Date(Date.now()).toTimeString()
const timeCreated = now.split(' ')[0]

const openContents = () => {
  ContentsOpen.value = true
}

const notifyMsg = ref('')
const notifyActive = ref(false)

/*
* const notify = (msg) => {
  if (notifyActive.value){
    // skip
    return
  }
  notifyMsg.value = msg
  notifyActive.value = true
  setInterval(() => {
    notifyActive.value = false
    notifyMsg.value = ''
  }, 3500)
}
* */

const activeTicketName = () => ticketName.value === '' ? 'No Title' : ticketName.value;

</script>

<template>
  <div class="ticket">
    <Icon
        icon="akar-icons:circle-x-fill"
        :inline="true"
        width="12"
        color="white"
        class="ticket-close-icon"
        @click="$emit('removed', index)"
    />
    <textarea v-model="ticketName" placeholder="Ticket name" class="ticket-title" rows="3" />
    <div v-if="notifyActive === true" class="ticket-notification">
      {{ notifyMsg }}
    </div>
    <br/>
    <button @click="openContents" class="ticket-button">Open</button>

    <div v-if="ContentsOpen === true" class="ticket-content-popup">
      <Icon icon="akar-icons:circle-x-fill" class="ticket-close-icon" @click="ContentsOpen = false"/>
      <!-- display contents nicely -->
      <p class="ticket-popup-title">
        {{ activeTicketName() }} - (Made at {{timeCreated}})
      </p>
      <hr/>
      <textarea v-model="ticketContents" placeholder="Ticket Description" class="ticket-popup-contents" rows="8">
      </textarea>
    </div>
  </div>
</template>

<script>
export default {
  name: "MellowTicket",
  props: {
    index: Number
  }
}
</script>

<style scoped>

.ticket {
  background-color: #283a50;

  flex-direction: row;
  margin: auto;
  position: relative;
  height: 80px;
  width: 90%;
  padding-top: 10px;
  border: 3px inset white;
}

.ticket-title {
  width: 80%;

  background-color: inherit;
  color: white;
  border: 0;
  text-align: center;
}

.ticket-close-icon{
  position: absolute;
  top: 10px;
  right: 5px;
  color: white;
}

.ticket-content-popup {
  position: fixed;
  width: 500px;
  height: 200px;
  top: 50%;
  left: 50%;
  margin-top: -100px; /* Negative half of height. */
  margin-left: -250px; /* Negative half of width. */

  background-color: #2c3e50;

  border: 2px solid black;
  z-index: 10000;
}

.ticket-popup-title {
  text-align: center;
  color: white;
}

.ticket-popup-contents {
  display: block;
  /* very weird percentage, overlaps at 100%. Fuck knows. */
  width: 98.9%;
  background-color: inherit;
  color: white;

  border: none;
}

.ticket-notification {
  display: inline-block;
  text-align: center;
  height: 20%;
  width: 100%;
}

textarea {
  resize: none;
}

textarea:focus {
  -moz-box-shadow: none;
  -webkit-box-shadow: none;
  box-shadow: none;
  outline: none;
}

hr {
  border-top: 2px solid #cdffff;
}

.ticket-button {
  /* terrible, I've messed something up and now I'm having to use black magic to center things... */
  position: absolute;
  margin: 0;
  top: 70%;
  left: 42%;
}
</style>