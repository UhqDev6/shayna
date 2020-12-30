<template>
  <div class="product">
  <HeaderShayna></HeaderShayna>
    <!-- Breadcrumb Section Begin -->
    <div class="breacrumb-section text-left">
        <div class="container">
            <div class="row">
                <div class="col-lg-12">
                    <div class="breadcrumb-text product-more">
                        <router-link to="/"><i class="fa fa-home"></i> Home</router-link>
                        <span>Detail</span>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <!-- Breadcrumb Section Begin -->

    <!-- Product Shop Section Begin -->
    <section class="product-shop spad page-details">
        <div class="container">
            <div class="row">
                <div class="col-lg-12">
                    <div class="row">
                        <div class="col-lg-6">
                            <div class="product-pic-zoom">
                                <img class="product-big-img" :src="gambar" alt="" />
                            </div>
                            <div class="product-thumbs" v-if="productDetails.galleries.length > 0">
                                <carousel class="product-thumbs-track ps-slider" :dots="false" :nav="false">
                                    <div
                                        v-for="ss in productDetails.galleries"
                                        :key="ss.id"
                                        class="pt" @click="changeImage(ss.photo)" :class="ss.photo == gambar ? 'active' : '' ">
                                        <img :src="ss.photo" alt="" />
                                    </div>

                                </carousel>
                            </div>
                        </div>
                        <div class="col-lg-6">
                            <div class="product-details text-left">
                                <div class="pd-title">
                                    <span>{{ productDetails.type }}</span>
                                    <h3>{{productDetails.name}}</h3>
                                </div>
                                <div class="pd-desc text-justify">
                                    <p v-html=" productDetails.description"></p>
                                    <h4>{{ productDetails.price }}</h4>
                                </div>
                                <div class="quantity">
                                    <a @click="saveKeranjang(productDetails.id)" href="#" class="primary-btn pd-cart">Add To Cart</a>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
    <!-- Product Shop Section End -->

    <RelatedProdukShayna></RelatedProdukShayna>

    <FooterShayna></FooterShayna>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import HeaderShayna from '../components/HeaderShayna';
import RelatedProdukShayna from '../components/RelatedProdukShayna';
import FooterShayna from '../components/FooterShayna';

import carousel from 'vue-owl-carousel';
import axios from 'axios';
export default {
  name: 'product',
  components: {
    HeaderShayna,
    RelatedProdukShayna,
    FooterShayna,
    carousel
  },
  data (){
      return {
      gambar : "",
      productDetails : [],
      keranjangUser: []
      };
  },
  methods: {
      changeImage (urlImage)
      {
          this.gambar = urlImage;
        //   console.log(this.idPoduct);
      },
      setDataPicture(data)
      {
          //replace object productDetail dengan data dari API 
          this.productDetails = data;
          // replace value gambar default dengan data dari API (Galleries)
          this.gambar = data.galleries[0].photo;
      },
      saveKeranjang(idProduct)
      {
          this.keranjangUser.push(idProduct);
          const parsed = JSON.stringify(this.keranjangUser);
          localStorage.setItem('keranjangUser', parsed);
      }
  },
  mounted() {
      if (localStorage.getItem('keranjangUser')) {
          try {
              this.keranjangUser = JSON.parse(localStorage.getItem('keranjangUser'));
          } catch (error) {
              localStorage.removeItem('keranjanguser');
          }
      }
      axios
      .get("http://shayna-backend.belajarkoding.com/api/products", {
          params : {
              id : this.$route.params.id
          }
      })
      .then(res => (this.setDataPicture(res.data.data)))
      .catch(err => console.log(err));
  },
};
</script>


<style scoped>
    .product-thumbs .pt {
        margin-right: 14px;
    }
</style>
