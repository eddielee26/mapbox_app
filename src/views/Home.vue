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
      message: "Welcome to Vue.js!",
      places: [
        {
          long: -74.50,
          lat: 40,
          description: "place 1"
        },
        {
          long: -87.635490,
          lat: 41.878910,
          description: "Sears Tower"
        },
        {
          long: -87.624039,
          lat: 41.899239,
          description: "John Hancock Center"
        }
      ]
    };
  },
  created: function() {},
  mounted: function() {
    mapboxgl.accessToken = 'pk.eyJ1IjoiZWRkaWVsZWU5MyIsImEiOiJjazF1ejR0NzExNzFpM2xwNGhlbmQ2b2p0In0.TWYYKg_6Lqkj4e9cDNd9XA';
    var map = new mapboxgl.Map({
      container: 'map', // container id
      style: 'mapbox://styles/mapbox/streets-v11', // stylesheet location
      center: [-74.50, 40], // starting position [lng, lat]
      zoom: 12 // starting zoom
    });
    // // create the popup
    // var popup = new mapboxgl.Popup({ offset: 25 })
    //   .setText('random place in NJ');
    // // create the marker
    // new mapboxgl.Marker()
    //   .setLngLat([-74.50, 40])
    //   .setPopup(popup) // sets a popup on this marker
    //   .addTo(map);

    this.places.forEach(function(place) {
      console.log(place);
      var popup = new mapboxgl.Popup({ offset: 25 })
        .setText(place.description);

      new mapboxgl.Marker()
        .setLngLat([place.long, place.lat])
        .setPopup(popup) // sets a popup on this marker
        .addTo(map);
    });

  },
  methods: {}
};
</script>