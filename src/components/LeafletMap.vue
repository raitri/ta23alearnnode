<script setup>
import L from 'leaflet';
import 'leaflet/dist/leaflet.css';
import 'leaflet/dist/images/marker-icon-2x.png';
import 'leaflet/dist/images/marker-icon.png';
import 'leaflet/dist/images/marker-shadow.png';
import { onMounted, useId, watch } from 'vue';

const {center, zoom} = defineProps(['center', 'zoom']);
const id = 'map-' + useId();
let map;

onMounted(() => {
    map = L.map(id).setView(center, zoom);
    L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
        maxZoom: 19,
        attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>'
    }).addTo(map);
    var latlngs = [
        [59.39763, 24.29904],
        [59.39750, 24.29906],
        [59.39758, 24.29996],
        [59.39771, 24.29991]
    ];
    var polygon = L.polygon(latlngs, {color: 'red'}).addTo(map);
    var marker = L.marker([59.39759, 24.29950]).addTo(map);
    var marker = L.marker([59.42708, 24.74337]).addTo(map);
});
watch(() => center, (center, oldCenter) => {
    console.log(center, oldCenter);
    map.panTo(center);
});
watch(() => zoom, (zoom) => {
    map.setZoom(zoom);
})
</script>

<template>
    <div :id="id"></div>
</template>

<style scoped>
div {
    height: 90vh;
}
</style>