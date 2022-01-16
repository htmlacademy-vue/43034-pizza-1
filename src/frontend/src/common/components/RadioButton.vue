<template>
  <label :class="labelClass">
    <input
      type="radio"
      :name="radioName"
      :value="radioValue"
      :class="{ 'visually-hidden': visuallyHidden }"
      checked
    />
    <component :is="titleTag">{{ title }}</component>
    <span v-if="description">{{ description }}</span>
  </label>
</template>

<script>
export default {
  name: "RadioButton",
  props: {
    labelClass: {
      type: String,
      required: false,
    },
    radioName: {
      type: String,
      required: true,
    },
    radioValue: {
      type: Number,
      required: true,
    },
    titleTag: {
      type: String,
      default: "span",
    },
    title: {
      type: String,
      required: true,
    },
    description: {
      type: String,
      required: false,
    },
    visuallyHidden: {
      type: Boolean,
      default: false,
    },
  },
};
</script>

<style scoped></style>
