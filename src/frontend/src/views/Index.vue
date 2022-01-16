<template>
  <div>
    <main class="content">
      <form action="#" method="post">
        <div class="content__wrapper">
          <h1 class="title title--big">Конструктор пиццы</h1>
          <BuilderDoughSelector :doughs-data="doughs" />
          <BuilderSizeSelector :sizes-data="sizes" />
          <BuilderIngredientsSelector
            :sauces-data="sauces"
            :ingredients-data="ingredients"
          />
          <BuilderPizzaView />
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
    };
  },
};
</script>

<style scoped></style>
