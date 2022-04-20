<template>
  <div class="form">
    <DxSelectBox
      v-model="formData.type"
      :items="form.type.items"
      :placeholder="form.type.placeholder"
    />
    <DxSelectBox
      v-model="formData.source"
      :items="form.source.items"
      :placeholder="form.source.placeholder"
      :disabled="!formData.type"
    />
    <DxButton
      :text="form.button.label"
      :disabled="!(formData.source && formData.type)"
      @click="handleSubmit"
    />
  </div>
</template>

<script>
import DxSelectBox from 'devextreme-vue/select-box';
import DxButton from 'devextreme-vue/button';

export default {
  components: {
    DxSelectBox,
    DxButton
  },
  data() {
    return {
      formData: {
        type: null,
        source: null
      },
      form: {
        type: {
          items: ['pie', 'line'],
          placeholder: 'Выберите тип графика',
        },
        source: {
          items: ['https://run.mocky.io/v3/2699115b-8ced-40c3-8072-b7fa9faf6047', 'https://run.mocky.io/v3/92a0a266-0321-4ff5-9993-b394d03ceee2'],
          placeholder: 'Выберите источник данных',
        },
        button: {
          label: 'Создать график'
        }
      }
    }
  },
  methods: {
    clearForm() {
      this.formData.source = null;
      this.formData.type = null;
    },
    handleSubmit () {
      this.$emit('submit', {
        type: this.formData.type,
        source: this.formData.source
      });
      this.clearForm();
    }
  },
}
</script>

<style scoped>
.form {
  width: 500px;
}
</style>