<template>
  <div id="app">
    <input type="number" v-model="zoom" style="position: absolute; z-index: 100">
    <app-map :zoom="zoom" :minZoom="3" :layers="map1Layers" :layerSwitcher="true"></app-map>
  </div>
</template>

<script>

import Tile from 'ol/layer/tile';
import OSM from 'ol/source/osm';

import appMap from './components/map.vue';

export default {
	name: 'app',
	components: { appMap },
	data () {
		return {
			zoom: 3,
      map1Layers: [
	      new Tile({
		      source: new OSM()
	      })
      ]
		}
	}
}
</script>

<style>
#app {
  padding: 0;
  margin: 0;
}
</style>
