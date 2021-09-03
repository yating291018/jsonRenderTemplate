🇻
<template>
  <Input
    type="text"
    v-model="InputValue"
    placeholder="请输入"
    @input="getInputValue"
  ></Input>
</template>
<script>
export default {
  name: "InputView",
  props: {
    value: {
      type: String,
      default: "",
    },
  },
  components: {},
  data() {
    return {
      InputValue: this.value,
    };
  },
  methods: {
    getInputValue() {
      this.$emit("input", this.InputValue);
    },
  },
};
</script>
<style lang="less" scoped></style>
