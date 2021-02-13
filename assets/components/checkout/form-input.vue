<template>
  <div class="form-group">
    <label
        for="customerName"
        class="col-form-label"
    >
      Name:
    </label>
    <input
        type="text"
        :class="{
          'is-invalid': !isFieldValid('customerName'),
          'form-control': true
        }"
        id="customerName"
        v-model.trim="form.customerName"
    >
    <span
        v-show="!isFieldValid('customerName')"
        class="invalid-feedback"
    >
      {{ validationErrors.customerName }}
    </span>
  </div>
</template>

<script>
export default {
  name: 'FormInput',
  methods: {
    isFieldValid(fieldName) {
      return !(fieldName in this.validationErrors)
    }
  },
};
</script>

<style scoped>

</style>
