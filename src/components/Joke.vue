<template>
  <div>
      <span>{{ joke }}</span>
      <div>
        <button @click="handleRequest">Give me another joke </button>
      </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'Joke',
    data() {
        return {
            joke: null,
        }
    },
    mounted () {
        this.handleRequest();
    },
    methods: {
        async handleRequest() {
            let response = await axios.get('https://icanhazdadjoke.com/', {
                headers: {'Accept': 'application/json'},
            });

            this.joke = response.data.joke
        }
    }
}
</script>

<style>
button {
    display:inline-block;
    padding:0.3em 1.2em;
    margin:0 0.1em 0.1em 0;
    border:0.16em solid rgba(255,255,255,0);
    border-radius:2em;
    box-sizing: border-box;
    text-decoration:none;
    font-family:'Roboto',sans-serif;
    font-weight:300;
    color:#FFFFFF;
    text-shadow: 0 0.04em 0.04em rgba(0,0,0,0.35);
    text-align:center;
    transition: all 0.2s;
    background-color: #9a4ef1;
}
button:hover{
    border-color: rgba(255,255,255,1);
}
</style>