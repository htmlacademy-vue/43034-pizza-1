<template>
  <div class="content__dough">
    <div class="sheet">
      <h2 class="title title--small sheet__title">Выберите тесто</h2>
      <div class="sheet__content dough">
        <label
          v-for="dough in doughsData"
          :key="dough.id"
          :class="`dough__input dough__input--${addClass(
            doughsClass,
            dough.id
          )}`"
          @click="$emit('change-dough', addClass(doughsClass, dough.id))"
        >
          <RadioButton
            radio-name="dought"
            :radio-value="dough.id"
            visually-hidden
            :checked="dough.id === 1"
          />
          <b>{{ dough.name }}</b>
          <span>{{ dough.description }}</span>
        </label>
      </div>
    </div>
  </div>
</template>

<script>
import RadioButton from "@/common/components/RadioButton";

export default {
  name: "BuilderDoughSelector",
  components: {
    RadioButton,
  },
  data() {
    return {
      doughsClass: [
        { id: 1, value: "light" },
        { id: 2, value: "large" },
      ],
    };
  },
  props: {
    doughsData: {
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
