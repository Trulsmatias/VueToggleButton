<script setup lang="ts">
import { processSlotOutlet } from '@vue/compiler-core';
import { ref, computed } from 'vue'

const props = defineProps({
    value: Boolean,
    leftLabel: String,
    rightLabel: String,
    isEndabled: Boolean
})

const emit = defineEmits(["emittedValued"])

function toggle() {
    if (!props.isEndabled) return;
    emit('emittedValued', !props.value);
}

const backgroundStyles = computed(() => {
    if (props.isEndabled) {
        return {
            'background-activated': props.value,
            'background-deactivated': !props.value
        };
    }
    return {
        'background-activated': props.value,
        'background-deactivated': !props.value
    };
})

const indicatorStyles = computed(() => {
    return { transform: props.value ? 'translateX(14px)' : 'translateX(0)' };
})

</script>

<template>
    <div class="horizontal-content">
        <p class="label-style">{{ leftLabel }}</p>
        <div>
            <span class="toggle-wrapper" role="checkbox" :aria-checked="value" tabindex="0" @click="toggle"
                @keydown.space.prevent="toggle">
                <span class="toggle-background" :class="backgroundStyles" />
                <span class="toggle-indicator" :style="indicatorStyles" />
            </span>
        </div>
        <p class="label-style">{{ rightLabel }}</p>
    </div>
</template>

<style>
.horizontal-content {
    display: flex;
    flex-direction: row;
}

.label-style {
    color: rgba(0, 0, 0, 0.9);
}


.background-activated {
    background-color: #518D6C;
}

.background-deactivated {
    background-color: #00000033;
}
.background-activated-disabled {
    background-color: #518D6C;
}

.background-deactivated-disabled {
    background-color: #0000001A;
;
}

.toggle-wrapper {
    display: inline-block;
    position: relative;
    cursor: pointer;
    width: 32px;
    height: 18px;
    border-radius: 9999px;
    margin: 0 10px;
}

.toggle-wrapper:focus {
    outline: 0;
}

.toggle-background {
    display: inline-block;
    border-radius: 9999px;
    height: 100%;
    width: 100%;
    box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.1);
    transition: background-color .4s ease;
}

.toggle-indicator {
    position: absolute;
    height: 14px;
    width: 14px;
    left: 2px;
    bottom: 2px;
    background-color: #ffffff;
    border-radius: 9999px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    transition: transform .4s ease;
}
</style>