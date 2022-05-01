<template>
  <view
    class="unitify-checkbox"
    :class="[
      {
        'unitify-checkbox--disabled': disabled == true,
      },
    ]"
    @click="handlerCheck(labelDisabled)"
  >
    <view
      class="unitify-checkbox--content"
      @click="handlerCheck(!labelDisabled)"
      :style="{
        '--checkbox-active-color': color,
        '--checkbox-height': size,
        '--checkbox-width': size,
      }"
      :class="{
        'unitify-checkbox--content--active': checked == true,

        'unitify-checkbox--content--round': shape === 'round',
        'unitify-checkbox--content--square': shape === 'square',
      }"
    >
      <svg
        v-show="checked"
        t="1651392657440"
        class="icon"
        viewBox="0 0 1024 1024"
        version="1.1"
        xmlns="http://www.w3.org/2000/svg"
        p-id="2922"
        :width="size"
        :height="size"
      >
        <path
          d="M203.776 495.762286l178.614857 114.541714 445.878857-364.836571 52.662857 51.346285-500.004571 486.546286L149.650286 545.645714l54.125714-49.883428z"
          p-id="2923"
          :fill="disabled && checked ? '#646566' : '#ffffff'"
        ></path>
      </svg>
    </view>
    <slot></slot>
  </view>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
export default defineComponent({
  name: "CheckBox",
  props: {
    modelValue: {
      type: Boolean,
    },
    checked: {
      type: Boolean,
      default: false,
    },
    shape: {
      type: String,
      default: "round",
    },
    disabled: {
      type: Boolean,
      default: false,
    },
    color: {
      type: String,
    },
    size: {
      type: String,
    },
    labelDisabled: {
      type: Boolean,
      default: false,
    },
  },
  emits: ["update:modelValue"],
  setup(props, { emit }) {
    const checked = ref(props.checked ? props.checked : props.modelValue);
    const handlerCheck = (labelDisabled: boolean) => {
      if (props.disabled) {
        return;
      }
      if (!labelDisabled) {
        checked.value = !checked.value;
        emit("update:modelValue", checked.value);
      }
    };
    return { handlerCheck, checked };
  },
});
</script>

<style lang="scss" scoped>
@import "checkbox.scss";
</style>
