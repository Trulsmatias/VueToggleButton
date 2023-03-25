<script setup lang="ts">
import Toggle from './components/Toggle.vue';
import { ref } from 'vue'
const leftLabelValue = "leftString"
const rightLabelValue = "rightString"
const toggleValue = ref(false);
const isToggleEnabled = true;
</script>

<template>
  <Toggle :value="toggleValue" @emittedValued="(val) => toggleValue = val" :left-label="leftLabelValue"
    :right-label="rightLabelValue" :isEndabled="isToggleEnabled" />
  <p>{{ toggleValue }}</p>
</template>

<style lang="scss"></style>
