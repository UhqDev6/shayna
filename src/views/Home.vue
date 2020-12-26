<template>
  <div class="home">
  <HeaderShayna></HeaderShayna>
  <CarosalShayna></CarosalShayna>
  <BannerShayna></BannerShayna>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import HeaderShayna from '../components/HeaderShayna';
import CarosalShayna from '../components/CarosalShayna';
import BannerShayna from '../components/BannerShayna';


export default {
  name: 'Home',
  components: {
    HeaderShayna,
    CarosalShayna,
    BannerShayna
  }
}
</script>
