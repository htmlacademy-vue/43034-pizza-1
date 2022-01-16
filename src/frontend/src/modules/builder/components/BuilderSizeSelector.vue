<template>
  <div class="content__diameter">
    <div class="sheet">
      <h2 class="title title--small sheet__title">Выберите размер</h2>
      <div class="sheet__content diameter">
        <RadioButton
          v-for="size in sizesData"
          :key="size.id"
          :label-class="`diameter__input diameter__input--${addClass(
            sizesClass,
            size.id
          )}`"
          radio-name="diameter"
          :radio-value="size.id"
          :title="size.name"
          visually-hidden
        />
      </div>
    </div>
  </div>
</template>

<script>
import RadioButton from "@/common/components/RadioButton";

export default {
  name: "BuilderSizeSelector",
  components: {
    RadioButton,
  },
  data() {
    return {
      sizesClass: [
        { id: 1, value: "small" },
        { id: 2, value: "normal" },
        { id: 3, value: "big" },
      ],
    };
  },
  props: {
    sizesData: {
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
