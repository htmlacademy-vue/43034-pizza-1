<template>
  <div>
    <header class="header">
      <div class="header__logo">
        <a href="index.html" class="logo">
          <img
            src="img/logo.svg"
            alt="V!U!E! Pizza logo"
            width="90"
            height="40"
          />
        </a>
      </div>
      <div class="header__cart">
        <a href="cart.html">0 ₽</a>
      </div>
      <div class="header__user">
        <a href="#" class="header__login"><span>Войти</span></a>
      </div>
    </header>
    <main class="content">
      <form action="#" method="post">
        <div class="content__wrapper">
          <h1 class="title title--big">Конструктор пиццы</h1>
          <div class="content__dough">
            <div class="sheet">
              <h2 class="title title--small sheet__title">Выберите тесто</h2>
              <div class="sheet__content dough">
                <label
                  v-for="dough in doughs"
                  :key="dough.id"
                  :class="`dough__input dough__input--${
                    doughsClass.find((elem) => elem.id === dough.id).value
                  }`"
                >
                  <input
                    type="radio"
                    name="dought"
                    :value="dough.id"
                    class="visually-hidden"
                    checked
                  />
                  <b>{{ dough.name }}</b>
                  <span>{{ dough.description }}</span>
                </label>
              </div>
            </div>
          </div>
          <div class="content__diameter">
            <div class="sheet">
              <h2 class="title title--small sheet__title">Выберите размер</h2>
              <div class="sheet__content diameter">
                <label
                  v-for="size in sizes"
                  :key="size.id"
                  :class="`diameter__input diameter__input--${
                    sizesClass.find((elem) => elem.id === size.id).value
                  }`"
                >
                  <input
                    type="radio"
                    name="diameter"
                    :value="size.id"
                    class="visually-hidden"
                  />
                  <span>{{ size.name }}</span>
                </label>
              </div>
            </div>
          </div>
          <div class="content__ingredients">
            <div class="sheet">
              <h2 class="title title--small sheet__title">
                Выберите ингредиенты
              </h2>
              <div class="sheet__content ingredients">
                <div class="ingredients__sauce">
                  <p>Основной соус:</p>
                  <label
                    v-for="sauce in sauces"
                    :key="sauce.id"
                    class="radio ingredients__input"
                  >
                    <input
                      type="radio"
                      name="sauce"
                      :value="sauce.id"
                      checked
                    />
                    <span>{{ sauce.name }}</span>
                  </label>
                </div>
                <div class="ingredients__filling">
                  <p>Начинка:</p>
                  <ul class="ingredients__list">
                    <li
                      v-for="ingredient in ingredients"
                      :key="ingredient.id"
                      class="ingredients__item"
                    >
                      <span
                        :class="`filling filling--${
                          ingredientsClass.find(
                            (elem) => elem.id === ingredient.id
                          ).value
                        }`"
                        >{{ ingredient.name }}</span
                      >
                      <div class="counter counter--orange ingredients__counter">
                        <button
                          type="button"
                          class="counter__button counter__button--minus"
                          disabled
                        >
                          <span class="visually-hidden">Меньше</span>
                        </button>
                        <input
                          type="text"
                          name="counter"
                          class="counter__input"
                          value="0"
                        />
                        <button
                          type="button"
                          class="counter__button counter__button--plus"
                        >
                          <span class="visually-hidden">Больше</span>
                        </button>
                      </div>
                    </li>
                  </ul>
                </div>
              </div>
            </div>
          </div>
          <div class="content__pizza">
            <label class="input">
              <span class="visually-hidden">Название пиццы</span>
              <input
                type="text"
                name="pizza_name"
                placeholder="Введите название пиццы"
              />
            </label>
            <div class="content__constructor">
              <div class="pizza pizza--foundation--big-tomato">
                <div class="pizza__wrapper">
                  <div class="pizza__filling pizza__filling--ananas"></div>
                  <div class="pizza__filling pizza__filling--bacon"></div>
                  <div class="pizza__filling pizza__filling--cheddar"></div>
                </div>
              </div>
            </div>
            <div class="content__result">
              <p>Итого: 0 ₽</p>
              <button type="button" class="button" disabled>Готовьте!</button>
            </div>
          </div>
        </div>
      </form>
    </main>
  </div>
</template>

<script>
import pizza from "@/static/pizza.json";

export default {
  name: "IndexHome",
  data() {
    return {
      doughs: pizza.dough,
      doughsClass: [
        { id: 1, value: "light" },
        { id: 2, value: "large" },
      ],
      sizes: pizza.sizes,
      sizesClass: [
        { id: 1, value: "small" },
        { id: 2, value: "normal" },
        { id: 3, value: "big" },
      ],
      ingredients: pizza.ingredients,
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
      sauces: pizza.sauces,
    };
  },
};
</script>

<style scoped></style>
