<template>
  <div class="content__ingredients">
    <div class="sheet">
      <h2 class="title title--small sheet__title">Выберите ингредиенты</h2>
      <div class="sheet__content ingredients">
        <div class="ingredients__sauce">
          <p>Основной соус:</p>
          <RadioButton
            v-for="sauce in saucesData"
            :key="sauce.id"
            label-class="radio ingredients__input"
            radio-name="sauce"
            :radio-value="sauce.id"
            :title="sauce.name"
          />
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
              <ItemCounter />
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
  },
};
</script>

<style scoped></style>
