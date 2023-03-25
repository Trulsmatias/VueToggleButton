<script setup lang="ts">
import type ChatToggleVue from './components/ChatToggle.vue';
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import ToggleItem from './components/ToggleItem.vue'
import ChatToggle from './components/ChatToggle.vue';
import TuturialToggle from './TuturialToggle.vue';
import { ref } from 'vue'
const leftLabelValue = "leftString"
const rightLabelValue = "rightString"
const toggleValue = ref(false);
const isToggleEnabled = true;
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it too!" />
    </div>
  </header>

  <main>
    <TheWelcome />
    <ToggleItem :leftLabel="leftLabelValue" v-bind:right-label="rightLabelValue" />
    <TuturialToggle :value="toggleValue" @emittedValued="(val) => toggleValue = val" left-label="hihi"
      right-label="hoho" :isEndabled="isToggleEnabled" />
    <p>{{ toggleValue }}</p>
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    /*flex-wrap: wrap;*/
  }
}
</style>
