<template>
  <Select v-model="selectValue" @on-change="getSelectValue" clearable>
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
      type: String,
      default: "",
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
      this.$emit("input", this.selectValue);
    },
  },
};
</script>
<style lang="less" scoped></style>
