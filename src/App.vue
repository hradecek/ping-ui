<template>
  <div id="app" class="bg-gray-100 h-screen flex-col justify-between items-center">    
    <img class="m-auto py-24" src="./assets/logo.png" alt="Vue logo" >    
    <div class="flex-1 flex justify-center w-full items-center">
      <Ping />
    </div>
  </div>
</template>

<script>
import Ping from './components/Ping.vue'

export default {
  name: 'app',
  components: {
    Ping
  }
}
</script>

