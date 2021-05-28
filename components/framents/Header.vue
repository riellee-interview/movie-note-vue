<template>
   <!-- Header-->
    <header class="movie-background py-5">
        <div class="container px-4 px-lg-5 my-5">
            <div class="text-center text-white">
                <h1 class="display-4 fw-bolder mb-5">상영영화</h1>
                <div class="dropdown">
                    <button class="btn btn-secondary dropdown-toggle" type="button" id="dropdownMenuButton1" data-bs-toggle="dropdown" aria-expanded="false">
                    {{ targetTitle }}
                    </button>
                    <ul class="dropdown-menu" aria-labelledby="dropdownMenuButton1">
                        <li><a class="dropdown-item" href="#" @click="searchBoxOfficeMovie('day')">일별 박스오피스 조회</a></li>
                        <li><a class="dropdown-item" href="#" @click="searchBoxOfficeMovie('week')">주간/주말 박스오피스 조회</a></li>
                    </ul>
                </div>
            </div>
        </div>
    </header>
</template>

<script>
export default {
    data: function() {
        return {
           targetTitle: '일별 박스오피스 조회'
        }
    },
    methods: {
        searchBoxOfficeMovie : function(target) {
            this.targetTitle = target === 'day' ? '일별 박스오피스 조회' : '주간/주말 박스오피스 조회';
            this.$emit('searchBoxOfficeMovie', target);
        }
    }
}
</script>

<style>

</style>