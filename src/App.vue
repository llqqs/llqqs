<script setup lang="ts">
import FormConfigurator from '@packages/FormConfigurator/src/index.vue'
import {reactive} from "vue";
import {type FormConfig, FormItemType} from "@packages/FormConfigurator/type";
import {cloneDeep} from 'lodash'

const formConfig = reactive<FormConfig>({
  formItems: [
    {
      type: FormItemType.RADIO,
      label: '性别',
      prop: 'gender',
      attribute: {
        options: [
          {
            value: 1,
            label: '男',
          },
          {
            value: 2,
            label: '女',
          }
        ],
      }
    },
    {
      type: FormItemType.CHECKBOX,
      label: '爱好',
      prop: 'hobby',
      attribute: {
        options: [
          {
            value: 1,
            label: '语文',
          },
          {
            value: 2,
            label: '数学',
          },
          {
            value: 3,
            label: '物理',
          }
        ],
      }
    },
    {
      type: FormItemType.INPUT,
      label: '姓名',
      prop: 'name',
    },
    {
      type: FormItemType.INPUT_NUMBER,
      label: '年龄',
      prop: 'age',
    },
    {
      type: FormItemType.SELECT,
      label: '政治面貌',
      prop: 'politicalOutlook',
      attribute: {
        options: [
          {
            value: 1,
            label: '党员',
          },
          {
            value: 2,
            label: '团员',
          }
        ],
      }
    },
    {
      type: FormItemType.CASCADER,
      label: '地址',
      prop: 'address',
      attribute: {
        options: [
          {
            value: '001',
            label: '北京市',
            children: [
              {
                value: '00101',
                label: '朝阳区',
              },
              {
                value: '00102',
                label: '海淀区',
              }
            ]
          },
          {
            value: '002',
            label: '重庆市',
            children: [
              {
                value: '00201',
                label: '渝北区',
              },
              {
                value: '00202',
                label: '江北区',
              },
              {
                value: '00203',
                label: '南岸区',
              }
            ]
          }
        ]
      }
    },
    {
      type: FormItemType.SWITCH,
      label: '是否通过',
      prop: 'whetherPass',
    },
    {
      type: FormItemType.SLIDER,
      label: '意愿度',
      prop: 'willingness',
    },
    {
      type: FormItemType.TIME_PICKER,
      label: '起床时间',
      prop: 'wakeUpTime',
    },
    {
      type: FormItemType.DATE_PICKER,
      label: '出生年月',
      prop: 'birthday',
    },
    {
      type: FormItemType.UPLOAD,
      label: '头像',
      prop: 'avatar',
    },
    {
      type: FormItemType.RATE,
      label: '评价',
      prop: 'rate',
    },
    {
      type: FormItemType.COLOR_PICKER,
      label: '喜欢的颜色',
      prop: 'color',
    },
  ]
})

const modelModel = reactive({
  name: '格子惊蛰版'
})

const formConfigReadonly = reactive<FormConfig>({
  ...cloneDeep(formConfig),
  attribute: {
    disabled: true,
  }
})
</script>

<template>
  <el-row :gutter="30">
    <el-col :span="12">
      <FormConfigurator
          :model="modelModel"
          :config="formConfig"
      />
    </el-col>
    <el-col :span="12">
      <FormConfigurator
          :model="modelModel"
          :config="formConfigReadonly"
      />
    </el-col>
  </el-row>
</template>

<style scoped>

</style>
