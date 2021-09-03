<template>
  <Select
    v-model="selectValue"
    @on-change="getSelectValue"
    multiple
    clearable
    :disabled="disabled"
  >
    <Option
      v-for="(item, index) in itemEnumConfigs"
      :key="index"
      :label="item.label"
      :value="item.value"
    ></Option>
  </Select>
</template>
<script>
export default {
  name: "",
  props: {
    value: {
      type: Array,
      default() {
        return [];
      },
    },
    itemEnumConfigs: {
      type: Array,
      default() {
        return [];
      },
    },
    disabled: {
      type: Boolean,
      default: false,
    },
  },
  components: {},
  data() {
    return {
      selectValue: this.value,
    };
  },
  methods: {
    getSelectValue() {
      // console.log("this.selectValue", this.selectValue);
      this.$emit("input", this.selectValue);
    },
  },
};
</script>
<style lang="less" scoped></style>
