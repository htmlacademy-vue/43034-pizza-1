<template>
  <div class="content__ingredients">
    <div class="sheet">
      <h2 class="title title--small sheet__title">Выберите ингредиенты</h2>
      <div class="sheet__content ingredients">
        <div class="ingredients__sauce">
          <p>Основной соус:</p>
          <label
            v-for="sauce in saucesData"
            :key="sauce.id"
            class="radio ingredients__input"
            @click="$emit('change-sauce', addClass(saucesClass, sauce.id))"
          >
            <RadioButton
              radio-name="sauce"
              :radio-value="sauce.id"
              :checked="sauce.id === 1"
            />
            <span>{{ sauce.name }}</span>
          </label>
        </div>
        <div class="ingredients__filling">
          <p>Начинка:</p>
          <ul class="ingredients__list">
            <li
              v-for="ingredient in ingredientsData"
              :key="ingredient.id"
              class="ingredients__item"
            >
              <SelectorItem
                :item-name="ingredient.name"
                :item-class="addClass(ingredientsClass, ingredient.id)"
              />
              <ItemCounter
                :data-ingredient="addClass(ingredientsClass, ingredient.id)"
                @ingredientsCounterHandler="ingredientsCounterHandler"
                :ref="`prod${ingredient.id}`"
                @click="inputValue($event, ingredient.id)"
              />
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import RadioButton from "@/common/components/RadioButton";
import SelectorItem from "@/common/components/SelectorItem";
import ItemCounter from "@/common/components/ItemCounter";

export default {
  name: "BuilderIngredientsSelector",
  components: {
    RadioButton,
    SelectorItem,
    ItemCounter,
  },
  data() {
    return {
      ingredientsClass: [
        { id: 1, value: "mushrooms" },
        { id: 2, value: "cheddar" },
        { id: 3, value: "salami" },
        { id: 4, value: "ham" },
        { id: 5, value: "ananas" },
        { id: 6, value: "bacon" },
        { id: 7, value: "onion" },
        { id: 8, value: "chile" },
        { id: 9, value: "jalapeno" },
        { id: 10, value: "olives" },
        { id: 11, value: "tomatoes" },
        { id: 12, value: "salmon" },
        { id: 13, value: "mozzarella" },
        { id: 14, value: "parmesan" },
        { id: 15, value: "blue_cheese" },
      ],
      saucesClass: [
        { id: 1, value: "tomato" },
        { id: 2, value: "creamy" },
      ],
      count: null,
      dataIngredients: [],
    };
  },
  props: {
    ingredientsData: {
      type: Array,
      required: true,
    },
    saucesData: {
      type: Array,
      required: true,
    },
  },
  methods: {
    addClass(arrName, id) {
      return arrName.find((elem) => elem.id === id).value;
    },
    ingredientsCounterHandler(value) {
      this.$emit("ingredientsCounterHandler", value);
    },
    inputValue(value, id) {
      const ingredientName =
        this.$refs["prod" + id][0].$attrs["data-ingredient"];
      let arrDataIngredients = this.dataIngredients;
      if (!this.dataIngredients.length) {
        this.dataIngredients.push({
          value: ingredientName,
          count: value,
        });
      }

      if (arrDataIngredients.length > 0) {
        let isHasIngredient = arrDataIngredients.find((post) => {
          return post.value === ingredientName;
        });
        if (!isHasIngredient) {
          this.dataIngredients.push({
            value: ingredientName,
            count: value,
          });
        } else {
          arrDataIngredients.find((post) => {
            if (post.value === ingredientName) {
              post.count = value;
            }
          });
          this.dataIngredients = arrDataIngredients;
        }
      }
      this.$emit("data-ingredients", this.dataIngredients);
    },
  },
};
</script>

<style scoped></style>
