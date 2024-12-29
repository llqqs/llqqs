<script setup lang="ts">
import {type FormConfig, FormItemType} from "@packages/FormConfigurator/type";

defineProps<{
  config: FormConfig,
  model: any
}>()
defineOptions({
  name: 'FormConfigurator',
})

</script>

<template>
  <el-form :model="model" v-bind="config.attribute">
    <el-row>
      <template v-for="item in config.formItems" :key="item.prop">
        <el-col v-if="FormItemType.RADIO == item.type">
          <el-form-item :label="item.label" :prop="item.prop">
            <el-radio-group v-model="model[item.prop]">
              <el-radio v-for="option in item.attribute?.options" :key="option.value" :label="option.value">
                {{ option.label }}
              </el-radio>
            </el-radio-group>
          </el-form-item>
        </el-col>
        <el-col v-if="FormItemType.CHECKBOX == item.type">
          <el-form-item :label="item.label" :prop="item.prop">
            <el-checkbox-group v-model="model[item.prop]">
              <el-checkbox v-for="option in item.attribute?.options" :key="option.value" :label="option.value">
                {{ option.label }}
              </el-checkbox>
            </el-checkbox-group>
          </el-form-item>
        </el-col>
        <el-col v-if="FormItemType.INPUT == item.type">
          <el-form-item
              :label="item.label" :prop="item.prop">
            <el-input
                v-model="model[item.prop]">
            </el-input>
          </el-form-item>
        </el-col>
        <el-col v-if="FormItemType.INPUT_NUMBER == item.type">
          <el-form-item :label="item.label" :prop="item.prop">
            <el-input-number
                v-model="model[item.prop]">
            </el-input-number>
          </el-form-item>
        </el-col>
        <el-col v-if="FormItemType.SELECT == item.type">
          <el-form-item
              :label="item.label" :prop="item.prop"
          >
            <el-select
                v-model="model[item.prop]"
            >
              <el-option v-for="option in item.attribute?.options" :key="option.value" :label="option.label"
                         :value="option.value"></el-option>
            </el-select>
          </el-form-item>
        </el-col>
        <el-col v-if="FormItemType.CASCADER == item.type">
          <el-form-item :label="item.label" :prop="item.prop">
            <el-cascader
                v-model="model[item.prop]"
                :options="item.attribute?.options">
            </el-cascader>
          </el-form-item>
        </el-col>
        <el-col v-if="FormItemType.SWITCH == item.type">
          <el-form-item :label="item.label" :prop="item.prop">
            <el-switch
                v-model="model[item.prop]">
            </el-switch>
          </el-form-item>
        </el-col>
        <el-col v-if="FormItemType.SLIDER == item.type">
          <el-form-item :label="item.label" :prop="item.prop">
            <el-slider
                v-model="model[item.prop]">
            </el-slider>
          </el-form-item>
        </el-col>
        <el-col v-if="FormItemType.TIME_PICKER == item.type">
          <el-form-item :label="item.label" :prop="item.prop">
            <el-time-select
                v-model="model[item.prop]">
            </el-time-select>
          </el-form-item>
        </el-col>
        <el-col v-if="FormItemType.DATE_PICKER == item.type">
          <el-form-item :label="item.label" :prop="item.prop">
            <el-date-picker
                type="date"
                v-model="model[item.prop]">
            </el-date-picker>
          </el-form-item>
        </el-col>
        <el-col v-if="FormItemType.UPLOAD == item.type">
          <el-form-item :label="item.label" :prop="item.prop">
            <el-upload>
            </el-upload>
          </el-form-item>
        </el-col>
        <el-col v-if="FormItemType.RATE == item.type">
          <el-form-item :label="item.label" :prop="item.prop">
            <el-rate v-model="model[item.prop]"></el-rate>
          </el-form-item>
        </el-col>
        <el-col v-if="FormItemType.COLOR_PICKER == item.type">
          <el-form-item :label="item.label" :prop="item.prop">
            <el-color-picker v-model="model[item.prop]"></el-color-picker>
          </el-form-item>
        </el-col>
      </template>
    </el-row>
  </el-form>
</template>