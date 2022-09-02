<template>
  <div class="content__result">
    <p>Итого: 0 ₽</p>
    <button type="button" class="button" :disabled="isDisableBtn">
      Готовьте!
    </button>
  </div>
</template>

<script>
export default {
  name: "BuilderPriceCounter",
  props: {
    isDisableBtn: {
      type: Boolean,
      default: true,
    },
  },
};
</script>

<style scoped></style>
