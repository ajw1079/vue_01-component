<template>
    <div class="img-wrapper">
        <div class="img-space">
            <!-- <img src="/img/cat_01.jpeg" alt="" class="w-100">     -->
            <img :src="src" alt="고양이" class="w-100">    
        </div>
        <div class="title-wrap">{{title}}</div>
    </div>    
</template>

<script>
export default {
    name: 'ImgCp',
    props: ['title', 'src']
    //부모로부터 전달 받은 데이터는 props로부터 받아온다.
}
</script>

<style lang="scss" scoped>
    .img-wrapper{
        border:1px solid #efefef;
        padding: 0.5em;
        border-radius: 0.4em;
        position: relative;
        margin-bottom: 20px;

        .img-space{
            width: 100%;
            height: 300px;

            img{
                width: 100%;
                height: 100%;
                object-fit: cover;
                opacity: 1;
                transition: all 0.5s;
                &:hover{
                    opacity: .75;
                }
            }
        }
        .title-wrap{
            width: calc(100% - 1em);
            position: absolute;
            left: 50%;
            bottom:0.5em;
            transform: translateX(-50%);
            padding:0.5em 0;
            background-color: #111;
            color:#fff;
            text-align: center;




        }
    }
</style>