<template>
  <div class="product">
  <HeaderShayna></HeaderShayna>
  <p>Product saya akan berada disini</p>
  <FooterShayna></FooterShayna>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import HeaderShayna from '../components/HeaderShayna';
import FooterShayna from '../components/FooterShayna';


export default {
  name: 'product',
  components: {
    HeaderShayna,
    FooterShayna
  }
}
</script>
