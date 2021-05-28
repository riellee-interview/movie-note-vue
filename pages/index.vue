<template>
  <div v-if="init">
        <Navigation />
        <Header />
        <!-- Section-->
        <section class="py-5">
            <div class="container px-4 px-lg-5 mt-5">
                <div id="dyCalendar"></div>
                <div class="row gx-4 gx-lg-5 row-cols-2 row-cols-md-3 row-cols-xl-4 justify-content-center">
                    <div v-for="item in movieList" class="col mb-5" v-bind:key="item.movieCd">
                        <div class="card h-100">
                            <!-- Product image-->
                            <a href="#"><img class="card-img-top" src="https://dummyimage.com/450x300/dee2e6/6c757d.jpg" alt="..." /></a>
                            <!-- Product details-->
                            <div class="card-body p-4">
                                <div class="text-center">
                                    <!-- Product name-->
                                    <h5 class="fw-bolder">{{item.movieNm}}</h5>
                                </div>
                            </div>
                            <!-- Product actions-->
                            <div class="card-footer p-4 pt-0 border-top-0 bg-transparent">
                                <div class="text-center">
                                    <!-- Product price-->
                                    {{item.showCnt.toString().replace(/\B(?<!\.\d*)(?=(\d{3})+(?!\d))/g, ",")}} 명
                                </div>
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


export default Vue.extend({
    data: function() {
        return {
            init : false,
            movieList : [],
            currentDt: ''
        }
    },
    components: { Navigation, Footer, Header },
    created() {
        // do nothing...
    },
    mounted() {
        this.currentDt = this.getFormatDate(new Date(), true);
        this.getDailyBoxOfficeMoives();
    },
    watch: {
        currentDt: function(date) {
            this.currentDt = date;
            this.getDailyBoxOfficeMoives();
        }
    },
    methods: {
        async getDailyBoxOfficeMoives() {
            const movieList = await this.$axios.$get(`http://kobis.or.kr/kobisopenapi/webservice/rest/boxoffice/searchDailyBoxOfficeList.json?key=ecbf42fb330b5ce4a401178c80e43323&targetDt=${this.currentDt}`);
            this.movieList = movieList.boxOfficeResult.dailyBoxOfficeList;
            this.init = true;
        },
        /**
         *  yyyyMMdd 포맷으로 반환
         */
        getFormatDate : function(date: { getFullYear: () => any; getMonth: () => any; getDate: () => any }, current: boolean) {
            var year = date.getFullYear();              //yyyy
            var month = (1 + date.getMonth());          //M 
            month = month >= 10 ? month : '0' + month;  //month 두자리로 저장
            
            var day = current ? date.getDate() - 1 : date.getDate();                   //d
            day = day >= 10 ? day : '0' + day;          //day 두자리로 저장
            return  year + '' + month + '' + day;       //'-' 추가하여 yyyy-mm-dd 형태 생성 가능
        }
    }
})
</script>

<style>

</style>
