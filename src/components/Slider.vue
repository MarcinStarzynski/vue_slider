<template>
    <div id="slider">
        <Slide
            v-for="item in bb" :key="item.id" 
            v-bind:name='item.name'
            v-bind:image='item.main_image'
            v-bind:desc='item.description'
            v-bind:images='item.images'
        />
    </div>
</template>

<script>
import axios from 'axios'
import Slide from './Slide.vue'

export default {
    name: 'Slider',

    data(){
        return {
            db: null,
            bb: null,
        }
    },

    components: {
        Slide
    },
    
    beforeMount(){
         this.getData();
         
        setTimeout(() => {
             this.slice();
         }, 500);

         setTimeout(() => {
             this.getCount();
         }, 1000);
    },

    methods: {
        slice() {
            this.bb= this.bb.slice(0, 20);
        },

        getCount() {
            let element = document.getElementById('slider').children;
            let i = 0;

            this.goNext(i, element);

        },

        goNext(child, parent) {
            const action1 = () => parent.item(child).classList.remove('active');
            const action2 = () => parent.item(child).classList.add('active');
            console.log(parent.length, parent, child);

            action2();
            setInterval(() => {
                if(child !== (parent.length - 1)){
                    action1()
                    child++
                    action2()
                } else {
                    action1()
                    child = 0;
                    action2()
                }
            }, 3000);
        },

        getData(){
            axios
            .get('http://localhost:8010/proxy/api/products?api_token=70876bc3a88f6644c53af702622edcd8')
            .then(response => (this.bb = response.data.data));
        }
    }
}
</script>

<style lang="scss">
    #slider {
        .active {
            display: block;
            color: #fff;
        }
        box-sizing: border-box;
        box-shadow: 12px 12px 40px rgba(0, 0, 0, 0.5);
        border-radius: 15px;
        background: rgba(9, 5, 43, 0.4);
        overflow: hidden;
        display: flex;
        flex-direction: row;
        align-items: center;
        height: 75vh;
        border-radius: 5%;
        width: 500px;
    }

    @media (min-width: 320px) and (max-width: 720px) {
        #slider {
           width: 280px;
           margin: 0 auto;
           height: 60vh;
        }
    }

</style>