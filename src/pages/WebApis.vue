<script setup>

function vibrate() {
    navigator.vibrate(200);
}

function SOS() {
    navigator.vibrate([100,30,100,30,100,200,200,30,200,30,200,200,100,30,100,30,100]);
}

function location() {
    navigator.geolocation.getCurrentPosition((event) => {
        console.log(event);
    }, (error) => {
        console.log('error', error);
    });
}

</script>

<template>
    <button @click="vibrate" class="button is-primary">Vibrate</button>
    <button @click="SOS" class="button is-primary">SOS</button>
    <button @click="location" class="button is-warning">Locate</button>
</template>