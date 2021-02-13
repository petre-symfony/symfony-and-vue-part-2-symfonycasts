<template>
  <div class="row p-3">
    <div class="col-12">
      <form >
        <div class="form-group">
          <label
              for="customerName"
              class="col-form-label"
          >
            Name:
          </label>
          <input
              type="text"
              id="customerName"
              v-model="form.customerName"
          >
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CheckoutForm',
  data() {
    return {
      form: {
        customerName: '',
        customerEmail: '',
        customerAddress: '',
        customerZip: '',
        customerCity: '',
        customerPhone: ''
      },
      validationErrors: {}
    }
  }
};
</script>

<style scoped>

</style>
