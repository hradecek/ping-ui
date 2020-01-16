<template>
  <div class="text-center">
  <div>
    <label for="url" class="mr-4">Website URL:</label>
    <input v-model="url" id="url" type="text" class="border border-solid border-gray-900 w-64 mr-4">
    <button @click="getPing" class="bg-green-600 hover:bg-blue-900 text-white font-bold py-2 px-4 rounded-full">Ping IT!</button>
  </div>
  <div class="flex justify-between items-center">
    <div v-if="response != ''" class="mr-6">
      <img v-if="isOK" class="h-16" src="../assets/ok.png" />
      <img v-if="!isOK" class="h-16" src="../assets/nok.png" />
    </div>
    <p>
      {{ response }}
    </p>
  </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Ping',
  data() {
    return {
      url: '',
      response: ''
    }    
  },
  computed: {
    isOK: function () {
      if (this.response['statusCode'] == 200) {
        return true
      } else {
        return false
      }
    }
  },
  methods: {
    getPing: function () {
      window.console.log(this.url)
      axios.post('https://ivdfpyb070.execute-api.eu-west-3.amazonaws.com/default/ping-service', {
        host: this.url
      })
           .then(response => this.response = response.data)
           .catch(error => this.response = error)
    }
  }
}
</script>