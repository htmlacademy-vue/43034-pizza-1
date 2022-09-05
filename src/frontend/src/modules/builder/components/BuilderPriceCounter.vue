<template>
  <div class="content__result">
    <p>Итого: {{ totalPrice }} ₽</p>
    <button type="button" class="button" :disabled="isDisableBtn">
      Готовьте!
    </button>
  </div>
</template>

<script>
export default {
  name: "BuilderPriceCounter",
  props: {
    totalPrice: {
      type: Number,
      default: 0,
    },
    isDisableBtn: {
      type: Boolean,
      default: true,
    },
  },
};
</script>

<style scoped></style>
