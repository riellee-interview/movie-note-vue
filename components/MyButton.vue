<template>
    <a class="btn btn-outline-dark mt-auto" :href=link><slot/></a>
</template>

<script>
export default {
    props: ['link']
}
</script>

<style>

</style>