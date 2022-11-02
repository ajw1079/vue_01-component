<template>
    <div class="container my-5">
        <ImgCp :title="title" :src="src"/>
        <ul class="thumb-wrap">
            <ThumbCp v-for="v in cat" :key="v.id" :img="v" />
            <!-- key라는 속성으로 고유값으로 갖고 있다가 Virtual DOM이 re-rendering을 할 수 있음 -->
        </ul>
    </div>
</template>

<script>
/*
1. 부모 컨포넌트가 자식 컴포넌트에게 변수를 전달 할 때에는 v-bind로 전달한다.
2. 자식 컴포넌트는 부모로부터 props로 변수를 전달받는다.
*/
import axios from 'axios'
import ImgCp from './components/ImgCp.vue'
import ThumbCP from './components/ThumbCp.vue'

export default {
    name: 'App',
    components: {ImgCp, ThumbCP},
    data() {
        return {
            cat : [],
            title: '',
            src: ''
        }
    },

    //#1
    beforeCreate(){
        console.log("beforeCreate");  //컴포넌트를 불러오기 전에 이벤트를 발생시킨다. 거의 사용할 일이 없음
    },
    //#2. [중요] 데이터를 불러오기 등의 DOM 으로 접근하기 전에 데이터를 가져온다. 데이터를 변수에 등록 (axios 또는 ajax를 통해 데이터를 가져온다.)
    async created() {
        console.log("create");  //html과 css가 생성되기 전에 실행된다.
        const {data} = await axios.get('/json/cat.json');
        console.log(data);
        this.cat = data;
        this.title = this.cat[1].title;
        this.src = this.cat[1].src;
    },
    //#3
    beforeMount(){
        console.log("beforeMount");  //
    },
    //#4. [중요] DOM으로 접근하여 데이터를 넣어준다. 대부분의 DOM 요소로 접근하여 화면이 구동되면서 함수를 실행한다.
    mounted() {
        console.log("mount");
    },
    //#5. DOM이 완성된 상태에서 데이터가 변할 때, 진행한다.
    beforeUpdate(){
        console.log("beforeMount");
    },
    //#6. [중요] 가상(virtual)의 DOM re-rendering / patch를 통해 DOM 내부의 데이터값을 변경하고 난 후에 진행한다.
    updated() {
        console.log("updated");
    },
    //#7. 웹처럼 메모리가 충분한 경우에는 관계 없으나 앱처럼 메모리가 부족한 경우 이하의 과정을 진행한다. 강제적으로 지울 필요가 있음.
    beforeUnmount() {
        console.log("beforeUnmount");
    },
    //#8. 앱에서는 홈버튼을 눌러서 숨겨놓는 단계가 unmount 단계임. 다시 열면 mount 단계가 됨
    unmounted() {
        console.log("unmount");
    },





}
</script>

<style lang="scss" scoped>
//각 컴포넌트에서 scoped의 역할은 고유값을 던져줄 수 있음 ===> .thumb-wrap[data-v-7ba5bd90]  ===> 다른 컴포넌트에서 동일한 명칭을 사용한다고 하더라도 겹쳐서 중복되는 현상을 막을 수 있음
//초기값을 설정하기 위해서는 scoped를 제거해야 전역으로 스타일을 적용할 수 있음. (예시)  ul, ol{padding:0; margin:0; list-style:none;}
    .thumb-wrap{
        padding: .5em;
        border: 1px solid #efefef;
        border-radius: .5em;
        display: flex;
        width: 101%;
    }
</style>