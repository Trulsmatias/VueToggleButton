<script setup lang="ts">
const props = defineProps({
    leftLabel: String,
    rightLabel: String
})
</script>

<template>
    <p>{{ leftLabel }}</p>
    <div id="toggleButton">
        <div id="toggleValueStart">
            First
        </div>

        <span class="dot"></span>
        <div id="toggleValueEnd">
            <span class="dot"></span>
        </div>
    </div>
    <p>{{ rightLabel }}</p>
</template>

<style>
p {
    display: inline;
}

h1 {
    display: inline;
}

.dot {
  height: 25px;
  width: 25px;
  background-color: #bbb;
  border-radius: 50%;
  display: inline-block;
}

.toggleValues {
    margin: 10em 10em;
}

#toggleButton {
    border: 1px solid #000;
    border-radius: 30px;
    display: flex;
    justify-content: space-between;
}

#toggleValueStart {
    background-color: yellow;
    height: 160;
    width: 160;
    border-radius: 10%;
    display: inline;
    margin: 10px 10px ;
}
#toggleValueEnd {
    background-color: teal;
    height: 160;
    width: 160;
    border-radius: 10%;
    display: inline;
    margin: 10px 10px ;
}
</style>