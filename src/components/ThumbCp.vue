<template>
    <li class="thumb">
        <img :src="img.src" :alt="img.title" class="w-100">
    </li>
</template>
<script>
export default {
    name: 'ThumbCp',
    props: ['img'] 
}
</script>
<style lang="scss" scoped>
    .thumb{
        margin-right: 1%;
        flex-grow: 1;
    }
</style>