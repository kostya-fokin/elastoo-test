<template>
<div class="container">
  <div
    v-if="list.length === 0"
    class="empty"
  >
    Пока нет ни одного графика
  </div>
  <ul
    v-else
    class="list"
  >
    <li
      v-for="(item, id) in list"
      :key="`chart-${id}`"
    >
      <ChartPie
        v-if="item.type === 'pie'"
        :data-source="item.data"
        :id="list.length - id"
      />
      <ChartLine
        v-else-if="item.type === 'line'"
        :data-source="item.data"
        :id="list.length - id"
      />
    </li>
  </ul>
  <ChartForm
    @submit="handleSubmit"
  />
</div>
</template>

<script>
import axios from 'axios';
import ChartPie from '@/components/chart-pie'
import ChartLine from '@/components/chart-line'
import ChartForm from '@/components/chart-form'

export default {
  components: {
    ChartPie,
    ChartLine,
    ChartForm,
  },
  data() {
    return {
      list: [],
    };
  },
  methods: {
    async createChart (type, source) {
      const { data } = await axios.get(source)
      this.list = [{ data, type }, ...this.list]
    },
    handleSubmit ({ type, source }) {
      this.createChart(type, source)
    }
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

.container {
  display: flex;
}

.list,
.empty {
  width: 700px;
}

.empty {
  text-align: center;
  padding: 40px;
}
</style>
