<template>
  <DatePicker
    :type="datetype"
    placeholder="请选择"
    :value="dateValue"
    @on-change="getDateValue"
  ></DatePicker>
</template>
<script>
// date、 daterange、 datetime、 datetimerange
export default {
  name: "",
  props: {
    datetype: {
      type: String,
      default: "date",
    },
    value: {
      type: [String, Array],
    },
  },
  components: {},
  data() {
    return {
      dateValue: this.value,
    };
  },
  methods: {
    getDateValue(value) {
      // console.log("dateValue", value);
      this.dateValue = value;
      this.$emit("input", value);
    },
  },
};
</script>
<style lang="less" scoped></style>
