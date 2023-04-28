<template>
  <div v-if="needRefresh" class="alert-reload" role="alert">
    <div class="message">
      <span v-if="needRefresh">
        New content available, click on reload button to update.
      </span>
    </div>
    <div class="btn-container">
      <button v-if="needRefresh" class="btn-reload" @click="updateServiceWorker()">
        Reload
      </button>
      <button @click="close" class="btn-close">Close</button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { useRegisterSW } from "virtual:pwa-register/vue";
const { needRefresh, updateServiceWorker } = useRegisterSW();

const close = () => {
  needRefresh.value = false;
}
</script>

<style scoped>
.alert-reload {
  width: auto;
  background: #abdbe3;
  border-radius: 8px;
  padding: 8px;
  margin: 8px;
  display: flex;
  justify-content: space-between;
}
.message {
  color: black;
  font-size: 0.8em;
}
.btn-container {
  display: flex;
  width: 100px;
  display: flex;
  justify-content: space-between;
}
button {
  padding: 6px;
  border-radius: 6px;
}
.btn-reload {
  color: #fff;
  font-size: 0.6em;
  background-color:cornflowerblue;
}
.btn-close {
  font-size: 0.6em;
  color: #fff;
  background: #000;
}
</style>
