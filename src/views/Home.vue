<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div id='map'></div>
  </div>
</template>

<style>
  body { 
    margin:0; 
    padding:0; 
  }
  #map { 
    top:0; 
    bottom:0; 
    height:500px; 
  }
</style>

<script>
/* global mapboxgl */
export default {
  data: function() {
    return {
      message: "Welcome to Vue.js!"
    };
  },
  created: function() {},
  mounted: function() {
    mapboxgl.accessToken = 'pk.eyJ1IjoiZWRkaWVsZWU5MyIsImEiOiJjazF1ejR0NzExNzFpM2xwNGhlbmQ2b2p0In0.TWYYKg_6Lqkj4e9cDNd9XA';
    var map = new mapboxgl.Map({
      container: 'map', // container id
      style: 'mapbox://styles/mapbox/streets-v11', // stylesheet location
      center: [-74.50, 40], // starting position [lng, lat]
      zoom: 9 // starting zoom
    });
  },
  methods: {}
};
</script>