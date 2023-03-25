<script setup lang="ts">
import { computed } from 'vue'

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
    if (!props.isEndabled) {
        return {
            'toggle__button--activated-disabled': props.value,
            'toggle__button--deactivated-disabled': !props.value
        };
    }
    return {
        'toggle__button--activated': props.value,
        'toggle__button--deactivated': !props.value
    };
})

const indicatorStyles = computed(() => {
    return {
        transform: props.value ? 'translateX(14px)' : 'translateX(0)',
        height: props.value ? '12px' : '8px',
        width: props.value ? '12px' : '8px',
        left: props.value ? '6px' : '4px',
        top: props.value ? '4px' : '6px',
    };
})

const leftLabelPadding = computed(() => {
    if (!props.leftLabel) return;
    return {
        margin: props.leftLabel ? '0px 10px 0px 0px' : '0px 0px 0px 0px'
    }
})

const rightLabelPadding = computed(() => {
    if (!props.rightLabel) return;
    return {
        margin: props.rightLabel ? '0px 0px 0px 10px' : '0px 0px 0px 0px'
    }
})

</script>

<template>
    <div class="toggle">
        <p class="toggle__label" :style="leftLabelPadding">{{ leftLabel }}</p>
        <div>
            <span class="toggle__wrapper" role="checkbox" :aria-checked="value" tabindex="0" @click="toggle"
                @keydown.space.prevent="toggle">
                <span class="toggle__background" :class="backgroundStyles" />
                <span class="toggle__indicator" :style="indicatorStyles" />
            </span>
        </div>
        <p class="toggle__label" :style="rightLabelPadding">{{ rightLabel }}</p>
    </div>
</template>

<style lang="scss">
$toggle-button-border-radius: 20px;

.toggle {
    display: flex;
    flex-direction: row;
}

.toggle__label {
    color: rgba(0, 0, 0, 0.9);
    font-size: 14px;
}

.toggle__button--activated {
    background-color: #518D6C;
}

.toggle__button--deactivated {
    background-color: #00000033;
}

.toggle__button--activated-disabled {
    background-color: #518D6CAF;
}

.toggle__button--deactivated-disabled {
    background-color: #0000001A;
}

.toggle__wrapper {
    display: inline-block;
    position: relative;
    cursor: pointer;
    width: 34px;
    height: 16px;
    border-radius: $toggle-button-border-radius;
}

.toggle__wrapper:focus {
    outline: 0;
}

.toggle__background {
    display: inline-block;
    border-radius: $toggle-button-border-radius;
    height: 100%;
    width: 100%;
    transition: background-color .4s ease;
}

.toggle__indicator {
    position: absolute;
    background-color: #ffffff;
    border-radius: 9999px;
    transition: transform .4s ease;
}
</style>