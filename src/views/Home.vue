<template>
  <div class="home">
    <Form
      ref="formRef"
      :model="formData"
      inline
      :label-width="80"
      :rules="rules"
    >
      <FormItem
        :prop="item.key"
        :label="item.itemDesc"
        v-for="(item, index) in formList"
        :key="index"
      >
        <component
          :is="item.type"
          v-model="formData[item.key]"
          :itemEnumConfigs="item.itemEnumConfigs"
          :datetype="item.datetype"
          style="width: 175px"
        ></component>
      </FormItem>
    </Form>
    <Button type="primary" @click="submit">提交</Button>
  </div>
</template>

<script>
// 输入， 单选，多选， 时间
// @ is an alias to /src
// 1. 两个组件有关系
import InputView from "../components/Input.vue";
import SelectView from "../components/Select";
import SelectMul from "../components/SelectMul.vue";
import DatePickerView from "../components/DatePicker.vue";
export default {
  name: "Home",
  data() {
    const check = (rules, value, callback) => {
      console.log("value", value);
      if (!value) {
        return callback(new Error("不能为空!"));
      }
      callback();
    };
    return {
      rules: {
        BankNo: [
          {
            required: true,
            message: "不能为空!",
            trigger: "blur",
          },
        ],
        origin: [
          {
            required: true,
            message: "不能为空",
            trigger: "change",
          },
        ],
        province: [
          {
            message: "不能为空",
            required: true,
            trigger: "change",
          },
        ],
        fut: [
          {
            required: true,
            message: "不能为空",
            trigger: "change",
            validator: check,
          },
        ],
        date1: [
          {
            required: true,
            message: "不能为空",
            trigger: "change",
            // validator: check,
          },
        ],
        date2: [
          {
            required: true,
            message: "不能为空",
            trigger: "change",
            // validator: check,
          },
        ],
        starttime: [
          {
            required: true,
            message: "不能为空",
            trigger: "change",
            validator: check,
          },
        ],
      },
      formData: {
        BankNo: "",
        origin: "",
        fut: [],
        date1: "",
        date2: "",
        starttime: [],
      },
      formList: [
        {
          type: "InputView",
          key: "BankNo",
          dependedFieldList: [],
          editStatus: "NOT_FORBIDDEN",
          initValue: "default",
          initValueDesc: "",
          isBackendDisplay: null,
          isFrontDisplay: true,
          isMust: 1,
          itemDesc: "银行卡号",
          itemEnumConfigs: [],
          itemMode: "INCOMING_BASIC_ITEM",
          itemSource: "",
        },
        {
          type: "SelectView",
          key: "origin",
          dependedFieldList: [],
          editStatus: "NOT_FORBIDDEN",
          initValue: "default",
          initValueDesc: "",
          isBackendDisplay: null,
          isFrontDisplay: true,
          isMust: 1,
          itemDesc: "国家",
          itemEnumConfigs: [
            {
              value: "中国",
              label: "中国",
            },
            {
              value: "usa",
              label: "usa",
            },
          ],
          itemMode: "INCOMING_BASIC_ITEM",
          itemSource: "",
        },
        {
          type: "SelectView",
          key: "province",
          dependedFieldList: [],
          editStatus: "NOT_FORBIDDEN",
          initValue: "default",
          initValueDesc: "",
          isBackendDisplay: null,
          isFrontDisplay: true,
          isMust: 1,
          itemDesc: "省份",
          itemEnumConfigs: [
            {
              value: "河南",
              label: "河南",
            },
            {
              value: "上海",
              label: "上海",
            },
          ],
          itemMode: "INCOMING_BASIC_ITEM",
          itemSource: "",
        },
        {
          type: "SelectMul",
          key: "fut",
          dependedFieldList: [],
          editStatus: "NOT_FORBIDDEN",
          initValue: "default",
          initValueDesc: "",
          isBackendDisplay: null,
          isFrontDisplay: true,
          isMust: 1,
          itemDesc: "水果",
          itemEnumConfigs: [
            {
              value: "apple",
              label: "apple",
            },
            {
              value: "orange",
              label: "orange",
            },
          ],
          itemMode: "INCOMING_BASIC_ITEM",
          itemSource: "",
        },
        {
          type: "DatePickerView",
          key: "date1",
          dependedFieldList: [],
          editStatus: "NOT_FORBIDDEN",
          initValue: "",
          initValueDesc: "",
          isBackendDisplay: null,
          isFrontDisplay: true,
          isMust: 1,
          itemDesc: "日期",
          itemEnumConfigs: [],
          itemMode: "INCOMING_BASIC_ITEM",
          itemSource: "",
        },
        {
          type: "DatePickerView",
          key: "date2",
          dependedFieldList: [],
          editStatus: "NOT_FORBIDDEN",
          initValue: "",
          initValueDesc: "",
          isBackendDisplay: null,
          isFrontDisplay: true,
          isMust: 1,
          itemDesc: "日期",
          itemEnumConfigs: [],
          itemMode: "INCOMING_BASIC_ITEM",
          itemSource: "",
        },
        {
          type: "DatePickerView",
          datetype: "datetimerange",
          key: "starttime",
          dependedFieldList: [],
          editStatus: "NOT_FORBIDDEN",
          initValue: "",
          initValueDesc: "",
          isBackendDisplay: null,
          isFrontDisplay: true,
          isMust: 1,
          itemDesc: "日期",
          itemEnumConfigs: [],
          itemMode: "INCOMING_BASIC_ITEM",
          itemSource: "",
        },
      ],
    };
  },
  components: {
    InputView,
    SelectView,
    SelectMul,
    DatePickerView,
  },
  methods: {
    submit() {
      console.log("data", this.formData);
      this.$refs.formRef.validate((valid) => {
        if (valid) {
          console.log("data", this.formData);
        }
      });
    },
  },
};
</script>
