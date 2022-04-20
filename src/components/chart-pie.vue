<template>
<DxPieChart
  :data-source="dataSource"
  palette="Bright"
  :title="`chart ${id}`"
>
  <DxSeries
    argument-field="Группа"
    value-field="Доля"
  >
    <DxLabel :visible="true">
      <DxConnector
        :visible="true"
        :width="1"
      />
    </DxLabel>
  </DxSeries>
  <DxSize :width="600"/>
</DxPieChart>
</template>

<script>
import DxPieChart, {
  DxSize,
  DxLabel,
  DxSeries,
  DxConnector,
} from 'devextreme-vue/pie-chart';

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
    DxLabel,
    DxSeries,
    DxConnector,
    DxPieChart
  }

}
</script>

<style>

</style>