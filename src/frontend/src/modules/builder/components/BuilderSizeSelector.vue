<template>
  <div class="content__diameter">
    <div class="sheet">
      <h2 class="title title--small sheet__title">Выберите размер</h2>
      <div class="sheet__content diameter">
        <label
          v-for="size in sizesData"
          :key="size.id"
          :class="`diameter__input diameter__input--${addClass(
            sizesClass,
            size.id
          )}`"
          @click="$emit('change-size', addClass(sizesClass, size.id))"
        >
          <RadioButton
            radio-name="diameter"
            :radio-value="size.id"
            visually-hidden
            :checked="size.id === 1"
          />
          <span>{{ size.name }}</span>
        </label>
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
