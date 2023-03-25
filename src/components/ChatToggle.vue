<template>
    <div class="toggle-switch" :class="{ 'toggle-switch--checked': isChecked, 'toggle-switch--disabled': isDisabled }">
      <div class="toggle-switch__label toggle-switch__label--left">{{ leftLabel }}</div>
      <div class="toggle-switch__control" @click="toggleSwitch" :aria-checked="isChecked" :aria-disabled="isDisabled">
        <div class="toggle-switch__slider"></div>
      </div>
      <div class="toggle-switch__label toggle-switch__label--right">{{ rightLabel }}</div>
    </div>
  </template>
  
  <script setup lang="ts">
  import { ref, defineEmits } from 'vue';
  
  const isChecked = ref(false);
  const isDisabled = ref(false);
  
  const leftLabel = 'Off';
  const rightLabel = 'On';
  
  const toggleSwitch = () => {
    if (!isDisabled.value) {
      isChecked.value = !isChecked.value;
      emit('update:modelValue', isChecked.value);
    }
  };
  
 const emit =  defineEmits(['update:modelValue']);

</script>
  
  <style lang="scss" scoped>
  .toggle-switch {
    display: flex;
    align-items: center;
    justify-content: space-between;
    position: relative;
    width: 100px;
    height: 50px;
    border-radius: 25px;
    background-color: #ccc;
    transition: background-color 0.2s;
    padding: 5px;
    box-sizing: border-box;
  
    &__label {
      font-size: 12px;
      font-weight: bold;
      text-transform: uppercase;
    }
  
    &__label--left {
      margin-right: 10px;
    }
  
    &__label--right {
      margin-left: 10px;
    }
  
    &__control {
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
      left: 5px;
      width: 40px;
      height: 40px;
      border-radius: 50%;
      background-color: #fff;
      cursor: pointer;
      transition: all 0.2s;
      box-sizing: border-box;
  
      &[aria-checked="true"] {
        left: calc(100% - 45px);
      }
  
      &:focus {
        outline: none;
        box-shadow: 0 0 0 2px #0074d9;
      }
  
      &:hover:not([aria-disabled="true"]) {
        transform: scale(1.1);
      }
  
      &:active:not([aria-disabled="true"]) {
        transform: scale()
      }
    }
}
</style>