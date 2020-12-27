<template>
  <div class="home">
  <HeaderShayna></HeaderShayna>
  <CarosalShayna></CarosalShayna>
  <BannerShayna></BannerShayna>
  <InstaShayna></InstaShayna>
  <ParnertShayna></ParnertShayna>
  <FooterShayna></FooterShayna>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import HeaderShayna from '../components/HeaderShayna';
import CarosalShayna from '../components/CarosalShayna';
import BannerShayna from '../components/BannerShayna';
import InstaShayna from '../components/InstaShayna';
import ParnertShayna from '../components/ParnertShayna';
import FooterShayna from '../components/FooterShayna';


export default {
  name: 'Home',
  components: {
    HeaderShayna,
    CarosalShayna,
    BannerShayna,
    InstaShayna,
    ParnertShayna,
    FooterShayna
  }
}
</script>
