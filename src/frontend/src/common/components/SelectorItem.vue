<template>
  <span :class="`filling filling--${itemClass}`">{{ itemName }}</span>
</template>

<script>
export default {
  name: "SelectorItem",
  props: {
    itemClass: {
      type: String,
      required: true,
    },
    itemName: {
      type: String,
      required: true,
    },
  },
};
</script>

<style scoped></style>
