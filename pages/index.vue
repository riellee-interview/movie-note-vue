<template>
  <div>
        <Navigation />
        <Header />
        <!-- Section-->
        <section class="py-5">
            <div class="container px-4 px-lg-5 mt-5">
                <div class="row gx-4 gx-lg-5 row-cols-2 row-cols-md-3 row-cols-xl-4 justify-content-center">
                    <MovieCard 
                        :isSale=false 
                        :src="'https://dummyimage.com/450x300/dee2e6/6c757d.jpg'" 
                        :productName="'Fancy Product'" 
                        :beforePrice="''" 
                        :productPrice="'$40.00 - $80.00'" 
                        :stars="0"/>
                    <MovieCard 
                        :isSale=true 
                        :src="'https://dummyimage.com/450x300/dee2e6/6c757d.jpg'" 
                        :productName="'Special Item'" 
                        :beforePrice="'$18.00'"  
                        :productPrice="'$18.00'" 
                        :stars="5"/>
                    <MovieCard 
                        :isSale=true 
                        :src="'https://dummyimage.com/450x300/dee2e6/6c757d.jpg'" 
                        :productName="'Sale Item'" 
                        :beforePrice="'$50.00'"  
                        :productPrice="'$25.00'" 
                        :stars="0"/>
                    <MovieCard 
                        :isSale=false 
                        :src="'https://dummyimage.com/450x300/dee2e6/6c757d.jpg'" 
                        :productName="'Popular Item'" 
                        :beforePrice="''"  
                        :productPrice="'$40.00'" 
                        :stars="5"/>
                    <MovieCard 
                        :isSale=false 
                        :src="'https://dummyimage.com/450x300/dee2e6/6c757d.jpg'" 
                        :productName="'Fancy Product'" 
                        :beforePrice="''" 
                        :productPrice="'$40.00 - $80.00'" 
                        :stars="0"/>
                    <MovieCard 
                        :isSale=true 
                        :src="'https://dummyimage.com/450x300/dee2e6/6c757d.jpg'" 
                        :productName="'Special Item'" 
                        :beforePrice="'$18.00'"  
                        :productPrice="'$18.00'" 
                        :stars="5"/>
                </div>
            </div>
        </section>
        <Footer />
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import Navigation from '~/components/framents/Navigation.vue'
import Header from '~/components/framents/Header.vue'
import Footer from '~/components/framents/Footer.vue'
import MovieCard from '~/components/MovieCard.vue'


export default Vue.extend({
  components: { MovieCard, Navigation, Footer, Header },})
</script>

<style>

</style>
