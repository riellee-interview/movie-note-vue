<template>
  <div>
        <Navigation />
        <Header />
        <!-- Section-->
        <section class="py-5">
            <div class="container px-4 px-lg-5 mt-5">
                <div class="row gx-4 gx-lg-5 row-cols-2 row-cols-md-3 row-cols-xl-4 justify-content-center">
                    <div v-for="item in movieList.dailyBoxOfficeList" class="col mb-5" v-bind:key="item.movieCd">
                        <div class="card h-100">
                            <!-- Product image-->
                            <img class="card-img-top" src="https://dummyimage.com/450x300/dee2e6/6c757d.jpg" alt="..." />
                            <!-- Product details-->
                            <div class="card-body p-4">
                                <div class="text-center">
                                    <!-- Product name-->
                                    <h5 class="fw-bolder">{{item.movieNm}}</h5>
                                    <!-- Product reviews-->
                                    <div class="d-flex justify-content-center small text-warning mb-2">
                                        <div class="bi-star-fill"></div>
                                        <div class="bi-star-fill"></div>
                                        <div class="bi-star-fill"></div>
                                        <div class="bi-star-fill"></div>
                                        <div class="bi-star-fill"></div>
                                    </div>
                                    <!-- Product price-->
                                    {{item.showCnt}}
                                </div>
                            </div>
                            <!-- Product actions-->
                            <div class="card-footer p-4 pt-0 border-top-0 bg-transparent">
                                <div class="text-center"><my-button :link="'#'">View Details</my-button></div>
                            </div>
                        </div>
                    </div>
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
    data: function() {
        return {
            movieList : {}
        }
    },
    components: { MovieCard, Navigation, Footer, Header },
    created() {
        this.getDailyBoxOfficeMoives();
    },
    mounted() {
        
    },
    methods: {
        async getDailyBoxOfficeMoives() {
            const movieList = await this.$axios.$get('http://kobis.or.kr/kobisopenapi/webservice/rest/boxoffice/searchDailyBoxOfficeList.json?key=ecbf42fb330b5ce4a401178c80e43323&targetDt=20210525');
            this.movieList = movieList;
        }
    }
})
</script>

<style>

</style>
