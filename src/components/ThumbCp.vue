<template>
    <li class="thumb">
        <img :src="img.src" :alt="img.title" class="w-100" @click="onChange">
    </li>
</template>
<script>
export default {
    name: 'ThumbCp',
    props: ['img'],
    methods : {
        onChange(e){
            this.$emit('@change', {src : e.target.src, title : e.target.alt })
            //$emit은 '내보내다'라는 의미 : 이벤트를 내보낸다.
        }
    }
}
</script>
<style lang="scss" scoped>
    .thumb{
        width: 25%;
        height: 100px;
        flex-grow: 1;
        border-radius: .25em;
        overflow: hidden;
        cursor: pointer;
        img{
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
    }
</style>