<template>
  <input
    type="radio"
    :name="radioName"
    :value="radioValue"
    :class="{ 'visually-hidden': visuallyHidden }"
  />
</template>

<script>
export default {
  name: "RadioButton",
  props: {
    radioName: {
      type: String,
      required: true,
    },
    radioValue: {
      type: Number,
      required: true,
    },
    visuallyHidden: {
      type: Boolean,
      default: false,
    },
  },
};
</script>

<style scoped></style>
