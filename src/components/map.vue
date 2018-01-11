<template>
	<div>
			<app-layer-switcher v-draggable v-if="layerSwitcher" :layers="layers"></app-layer-switcher>
		<div id="map"></div>
	</div>
</template>

<script>
	
	import draggable from 'vuedraggable';
	
	import appLayerSwitcher from './layer-switcher.vue';
	
	import Map from 'ol/map';
	import View from 'ol/view';
	import Tile from 'ol/layer/tile';
	import OSM from 'ol/source/osm';
	import Collection from 'ol/collection';
	
	export default {
		components: { appLayerSwitcher, draggable },
		name: 'app-map',
		props: {
			layers: {
				default: [],
				type: [ Array, Collection ]
			},
			zoom: {
				default: this.minZoom
			},
			minZoom: {
				default: 3
			},
			layerSwitcher: {
				default: false,
				type: Boolean
			}
		},
		data() {
			return {
				map : new Map({
					view: new View({
						center: [40, 40],
						zoom: this.zoom,
						minZoom: this.minZoom
					}),
					layers: this.layers
				})
			}
		},
		mounted()
		{
			this.map.setTarget('map');
		},
		watch:
		{
			zoom: function( zoomValue )
			{
				if( zoomValue.length )
				{
					this.map.getView().animate( { zoom: zoomValue} );
				}
			},
		}
	}
</script>

<style>
	#map {
		height: 100vh;
		width: 100vw;
		padding: 0;
		margin: 0;
	}
</style>