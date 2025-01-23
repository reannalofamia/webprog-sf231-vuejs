<template>
    <div v-on:click="countClicks">
      <h2>{{ name }}</h2>  
      <p>{{ message }}</p>
      <p id="red">You have clicked me {{ clicks }} times.</p>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        name: 'Banana',
        message: 'I like Bananas',
        clicks: 0
      }
    },
    methods: {
      countClicks() {
        this.clicks++;
      }
    }
  }
  </script>
  
  <style>
  #app > div {
    border: dashed black 1px;
    display: inline-block;
    width: 120px;
    margin: 10px;
    padding: 10px;
    background-color: yellow;
  }
  
  #app > div:hover {
    cursor: pointer;
  }
  </style>