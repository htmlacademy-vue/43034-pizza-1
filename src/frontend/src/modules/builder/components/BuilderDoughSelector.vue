<template>
  <div class="content__dough">
    <div class="sheet">
      <h2 class="title title--small sheet__title">Выберите тесто</h2>
      <div class="sheet__content dough">
        <RadioButton
          v-for="dough in doughsData"
          :key="dough.id"
          :label-class="`dough__input dough__input--${addClass(
            doughsClass,
            dough.id
          )}`"
          radio-name="dought"
          :radio-value="dough.id"
          title-tag="b"
          :title="dough.name"
          :description="dough.description"
          visually-hidden
        />
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
