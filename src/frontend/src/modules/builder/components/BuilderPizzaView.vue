<template>
  <div class="content__pizza">
    <label class="input">
      <span class="visually-hidden">Название пиццы</span>
      <input
        type="text"
        name="pizza_name"
        placeholder="Введите название пиццы"
        v-model="namePizza"
      />
    </label>
    <div class="content__constructor">
      <div :class="`pizza pizza--foundation--${setDough}-${sauce}`">
        <div class="pizza__wrapper">
          <template v-if="ingredientsList">
            <div
              v-for="(ingredient, index) in ingredientsList"
              :class="`pizza__filling ${ingredientsClass(ingredient, index)}`"
              :key="index"
            ></div>
          </template>
        </div>
      </div>
    </div>
    <BuilderPriceCounter :is-disable-btn="isDisableBtn()" />
  </div>
</template>

<script>
import BuilderPriceCounter from "@/modules/builder/components/BuilderPriceCounter";

export default {
  name: "BuilderPizzaView",
  components: {
    BuilderPriceCounter,
  },
  props: {
    dough: {
      type: String,
      required: true,
    },
    size: {
      type: String,
      required: true,
    },
    sauce: {
      type: String,
      required: true,
    },
    ingredientsList: {
      type: Array,
    },
  },
  data() {
    return {
      namePizza: "",
    };
  },
  computed: {
    setDough() {
      return this.dough === "light" ? "small" : "big";
    },
  },
  methods: {
    ingredientsClass(elem, index) {
      if (index >= 0) {
        if (elem.count === 1) {
          return "pizza__filling--" + elem.value;
        } else if (elem.count === 2) {
          return "pizza__filling--" + elem.value + " pizza__filling--second";
        } else if (elem.count === 3) {
          return "pizza__filling--" + elem.value + " pizza__filling--third";
        }
      }
    },
    isDisableBtn() {
      return this.namePizza !== "" && this.ingredientsList?.length > 0
        ? false
        : true;
    },
  },
};
</script>

<style scoped></style>
