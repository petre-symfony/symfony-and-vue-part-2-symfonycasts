<template>
  <div :class="[$style.component, 'container-fluid']">
    <div class="row">
      <aside class="col-xs-12 col-lg-3" />
      <div class="col-xs-12 col-lg-9">
        <title-component text="Shopping Cart" />
        <div class="content p-3">
         <loading v-if="cart === null" />
         <div v-if="cart !== null">
           <div
               v-for="(cartItem, index) in cart.items"
               :key="index"
           >
             {{ cartItem.product }} {{ cartItem.quantity }}
           </div>
           <div v-if="cart.items.length === 0">
             Your cart is empty! Get to shopping!
           </div>
         </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import TitleComponent from '@/components/title'
import ShoppingCartMixin from '@/mixins/get-shopping-cart'
import Loading from '@/components/loading'
import { fetchProductsById } from '@/services/products-service'

export default {
  name: 'ShoppingCart',
  mixins: [ShoppingCartMixin],
  components: {
    TitleComponent,
    Loading
  },
  watch: {
    async cart() {
      const productIds = this.cart.items.map((item) => item.product)
      const productResponse = await fetchProductsById(productIds)
      const products = productResponse.data['hydra:member'];

      const completeItems = this.cart.items.map((cartItem) => (
        {
          product: products.find((product) => product['@id'] === cartItem.product),
          color: cartItem.color,
          quantity: cartItem.quantity
        }
      ))

      console.log(completeItems)
    }
  }
};
</script>
<style lang="scss" module>
@import '~styles/components/light-component.scss';
.component :global {
  .content {
    @include light-component;
  }
}
</style>