<template>
  <q-page class="flex flex-center">
    <GmapMap
      :center="{lat: 53.404625, lng: 49.474948}"
      :zoom="7"
      style="width: 100%; height: 100vh"
      @click="setMarker($event)"
    >
      <GmapMarker
        :key="m.id"
        v-for="(m, index) in markers"
        :position="m.position"
        :clickable="true"
        :draggable="true"
        @click="getMarkerId(index)"
      />
    </GmapMap>
  </q-page>
</template>

<style>
</style>

<script>
export default {
  name: 'PageIndex',
  data() {
    return {
      markers: [
        {
          position: {
            lat: 53.404625, lng: 49.474948,
          },
          id: 12,
        },
      ],
    };
  },
  methods: {
    setMarker(target) {
      const { lat, lng } = target.latLng;
      this.markers.push(
        { position: { lat: lat(), lng: lng() } },
      );
    },
    getMarkerId(index) {
      this.markers.splice(index, 1);
    },
  },
};
</script>
