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
      // ingredientValue: "",
      // dataIngredients: [],
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
      //console.log(ingredient);
      ++this.inputValue;
      // this.ingredientValue = ingredient;
      // if (!this.dataIngredients.length) {
      //   this.dataIngredients.push({
      //     value: ingredient,
      //     count: this.inputValue,
      //   });
      // } else {
      //   this.dataIngredients.map((post) =>
      //     post.value === ingredient
      //       ? (post.count = this.inputValue)
      //       : this.dataIngredients.push({
      //           value: ingredient,
      //           count: this.inputValue,
      //         })
      //   );
      //   console.log("this.dataIngredients", this.dataIngredients);
      // }
      // const newPosts = posts.map((post) => (
      //   post.id === 1
      //     ? { ...post, text: 'other text' }
      //     : post
      // ));
      //console.log("this.dataIngredients", this.dataIngredients);
      // this.dataIngredients[this.inputValue] = ingredient;
      // return this.inputValue;
      //return { value: ingredient, count: this.inputValue };
      return this.inputValue;
    },
    minus() {
      --this.inputValue;
      // this.ingredientValue = ingredient;
      // // this.dataIngredients = this.dataIngredients.filter(function (f) {
      // //   return f !== ingredient;
      // // });
      // this.dataIngredients.map((post) =>
      //   post.value === ingredient ? (post.count = this.inputValue) : post
      // );
      // console.log("this.dataIngredients", this.dataIngredients);
      // console.log(
      //   "this.filterByProp(this.dataIngredients, ingredient)",
      //   this.filterByProp(this.dataIngredients, ingredient)
      // );
      // this.filterByProp(this.dataIngredients, ingredient);
      // return this.inputValue;
      return this.inputValue;
    },
    // filterByProp(arr, prop) {
    //   const seen = {};
    //   return arr.filter((item) => {
    //     console.log("item", item);
    //     console.log(seen[item[prop]]);
    //     if (seen[item[prop]]) {
    //       return false;
    //     } else {
    //       seen[item[prop]] = true;
    //       return true;
    //     }
    //   });
    // },
  },
};
</script>

<style scoped></style>
