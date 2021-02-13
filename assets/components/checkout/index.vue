<template>
  <div class="row p-3">
    <div class="col-12">
      <form >
        <div class="form-row">
          <form-input
            v-model="form.customerName"
            class="col"
            v-bind="getFieldProps('customerName', 'Name:')"
          />
          <form-input
            v-model="form.customerEmail"
            class="col"
            type="email"
            v-bind="getFieldProps('customerEmail', 'Email:')"
          />
        </div>
        <form-input
          v-model="form.customerAddress"
          v-bind="getFieldProps('customerAddress', 'Address:')"
        />
        <div class="form-row">
          <form-input
            class="col"
            v-model="form.customerZip"
            v-bind="getFieldProps('customerZip', 'Zip Code:')"
          />
          <form-input
            class="col"
            v-model="form.customerCity"
            v-bind="getFieldProps('customerCity', 'City:')"
          />
          <form-input
            class="col"
            type="tel"
            v-model="form.customerPhone"
            v-bind="getFieldProps('customerPhone', 'Phone Number:')"
          />
        </div>

        <div class="form-row justify-content-end align-items-center">
          <div class="col-auto">
            <button
                type="submit"
                class="btn btn-info btn-lg"
            >
              Order
            </button>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import FormInput from '@/components/checkout/form-input'

export default {
  name: 'CheckoutForm',
  components: {
    FormInput
  },
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
      validationErrors: {},
      loading: false
    }
  },
  methods: {
    getFieldProps(id, label) {
      return {
        id,
        label,
        errorMessage: this.validationErrors[id]
      }
    }
  },
};
</script>

<style scoped>

</style>
