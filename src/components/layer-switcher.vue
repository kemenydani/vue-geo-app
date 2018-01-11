<template>
	<div id="layerSwitcher">
		<ul id="demo">
			<app-layer class="item" :model="data"></app-layer>
		</ul>
		<button @click="change()">Change!</button>
	</div>
</template>

<script>
	
	import layer from './layer.vue';
	
	import Tile from 'ol/layer/tile';
	import OSM from 'ol/source/osm';
	import Collection from 'ol/collection';
	
	export default {
		name: 'layer-switcher',
		components: {
			'app-layer' : layer
		},
		props: {
			layers: {
				default: [],
				type: [ Array, Collection ]
			},
		},
		data() {
			return {
				data: {
					name: 'My Tree',
					children: [
						{ name: 'hello' },
						{ name: 'wat' },
						{
							name: 'child folder',
							children: [
								{
									name: 'child folder',
									children: [
										{ name: 'hello' },
										{ name: 'wat' }
									]
								},
								{ name: 'hello' },
								{ name: 'wat' },
								{
									name: 'child folder',
									children: [
										{ name: 'hello' },
										{ name: 'wat' }
									]
								}
							]
						}
					]
				}
			}
		},
		mounted() {
			console.log('new component mounted');
		},
		methods:
		{
			change()
			{
				this.$emit('change', 1)
			},
			addLayer( layer ){
			
			},
			addLayerAt( index ){
			
			},
			removeLayer(){
			
			}
		}
	}
</script>

<style>
	#layerSwitcher {
		position: absolute;
		z-index: 100;
		background: red;
		height: 300px;
		width: 200px;
		top: 100px;
	}
	.item {
		cursor: pointer;
	}
	.bold {
		font-weight: bold;
	}
	ul {
		padding-left: 1em;
		line-height: 1.5em;
		list-style-type: dot;
	}
</style>