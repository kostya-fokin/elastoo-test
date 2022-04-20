<template>
<DxChart
  :data-source="dataSource"
  palette="Bright"
  :title="`chart ${id}`"
>
  <DxCommonSeriesSettings
    type="line"
    argument-field="Дата"
  />
  <DxSeries
    value-field="Процент"
    name="Процент"
  />
  <DxSize :width="600"/>
</DxChart>
</template>

<script>
import {
  DxSize,
  DxChart,
  DxSeries,
  DxCommonSeriesSettings,
} from 'devextreme-vue/chart';

export default {
  props: {
    dataSource: {
      required: true,
      type: Array,
    },
    id: {
      required: true,
      type: Number
    }
  },
  components: {
    DxSize,
    DxChart,
    DxSeries,
    DxCommonSeriesSettings,
  }

}
</script>

<style>

</style>