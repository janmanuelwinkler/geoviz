<template>
  <v-container fluid>
    <v-row>
      <v-col cols="12" no-gutters>
        <div id="map" class="map-container"></div>   
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup lang="ts">

import { onMounted, ref } from 'vue'
import maplibregl from 'maplibre-gl'
import { Protocol, PMTiles } from 'pmtiles'
import 'maplibre-gl/dist/maplibre-gl.css'

// we declare the maplibregl.Map object here, as in more complex components
// you may want to access the objects from other method
// than the onMounted
const mapGl = ref<maplibregl.Map|null>(null);

onMounted(async () => {

  // add the pmtiles protocol
  var p = addPMTilesProtocol()

  // create the map object, bind it to the 'map' div in the template
  mapGl.value = new maplibregl.Map({
    container: 'map',
    style: 'https://geovizbucket.s3.us-west-2.amazonaws.com/osm_basempa_style.json'
  })

  // add controls
  mapGl.value?.addControl(new maplibregl.NavigationControl(), 'top-right')

  // zoom center the map
  const header = await p.getHeader()
  mapGl.value?.setZoom(header.maxZoom - 3)
  mapGl.value?.setCenter([header.centerLon, header.centerLat])

  // add sources and layers
  addPmTilesSourceAndLayer()
})

function addPMTilesProtocol()
{
  // create a protocol and a source(s) to it
  const protocol = new Protocol()
  // add PM Tiles protocol
  maplibregl.addProtocol('pmtiles', protocol.tile)
  const PMTILES_URL = "https://geovizbucket.s3.us-west-2.amazonaws.com/swiss_gemeinden.pmtiles"
  const p = new PMTiles(PMTILES_URL)
  protocol.add(p)
  return p
}

function addPmTilesSourceAndLayer()
{
  // add source
  const sourceId = "swiss_gemeinden"
  mapGl.value?.addSource(sourceId, {
    type: "vector",
    url: 'pmtiles://https://geovizbucket.s3.us-west-2.amazonaws.com/swiss_gemeinden.pmtiles'
  });

  // add layer
  const layerId = "gdf_gemeinden"
  mapGl.value?.addLayer({
    id: layerId,
    source: sourceId,
    'source-layer': layerId,
    type: 'fill',
    paint: {
      'fill-color': 'blue',
      'fill-outline-color': 'red',
      'fill-opacity': 0.3
    }
  });
}

</script>

<style scoped>

.map-container {
  width: 100%;
  height: 500px;
  margin-left: auto;
  margin-right: auto;
}

</style>