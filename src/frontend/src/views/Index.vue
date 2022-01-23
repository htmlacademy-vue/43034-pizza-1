<template>
  <div>
    <main class="content">
      <form action="#" method="post">
        <div class="content__wrapper">
          <h1 class="title title--big">Конструктор пиццы</h1>
          <BuilderDoughSelector
            :doughs-data="doughs"
            @change-dough="dough = $event"
          />
          <BuilderSizeSelector
            :sizes-data="sizes"
            @change-size="size = $event"
          />
          <BuilderIngredientsSelector
            :sauces-data="sauces"
            @change-sauce="sauce = $event"
            :ingredients-data="ingredients"
          />
          <BuilderPizzaView :dough="dough" :size="size" :sauce="sauce" />
        </div>
      </form>
    </main>
  </div>
</template>

<script>
import pizza from "@/static/pizza.json";
import BuilderDoughSelector from "@/modules/builder/components/BuilderDoughSelector";
import BuilderSizeSelector from "@/modules/builder/components/BuilderSizeSelector";
import BuilderIngredientsSelector from "@/modules/builder/components/BuilderIngredientsSelector";
import BuilderPizzaView from "@/modules/builder/components/BuilderPizzaView";

export default {
  name: "IndexHome",
  components: {
    BuilderDoughSelector,
    BuilderSizeSelector,
    BuilderIngredientsSelector,
    BuilderPizzaView,
  },
  data() {
    return {
      doughs: pizza.dough,
      sizes: pizza.sizes,
      ingredients: pizza.ingredients,
      sauces: pizza.sauces,
      size: "small",
      dough: "light",
      sauce: "tomato",
    };
  },
};
</script>

<style scoped></style>
