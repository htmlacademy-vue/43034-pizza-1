<template>
  <div class="counter counter--orange ingredients__counter">
    <button
      type="button"
      class="counter__button counter__button--minus"
      @click="$emit('click', minus())"
      :disabled="isDisabled('minus')"
    >
      <span class="visually-hidden">Меньше</span>
    </button>
    <input
      type="text"
      name="counter"
      class="counter__input"
      :value="inputValue"
    />
    <button
      type="button"
      class="counter__button counter__button--plus"
      @click="$emit('click', plus())"
      :disabled="isDisabled('plus')"
    >
      <span class="visually-hidden">Больше</span>
    </button>
  </div>
</template>

<script>
export default {
  name: "ItemCounter",

  data() {
    return {
      inputValue: 0,
    };
  },
  methods: {
    isDisabled(item) {
      return (
        (this.inputValue < 1 && item === "minus") ||
        (this.inputValue >= 3 && item === "plus")
      );
    },
    plus() {
      ++this.inputValue;
      return this.inputValue;
    },
    minus() {
      --this.inputValue;
      return this.inputValue;
    },
  },
};
</script>

<style scoped></style>
