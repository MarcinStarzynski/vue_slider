<template>
    <div class="slide"  @mouseover="hover = true" @mouseleave="hover = false">
        <h4>{{name}}</h4>
        <div class='image'>
            <img v-if="!hover" v-bind:src='image' />
            <img v-if="hover" v-bind:src='hoverImage' />
        </div>
        <p v-if="!show" @click="show = true">{{description}}</p>
        <p v-if="show">{{desc}}</p>
    </div>
</template>

<script>
export default {
    name: 'Slide',

    data(){
        return {
            hover: false,
            show: false,
        } 
    },

    props: {
        name: String,
        desc: String,
        image: String,
        images: Array,

    },

    computed: {

        description() {
            if(this.desc.length >= 30) {
                let short = this.desc.slice(0, 30);
                return short + '...'
            } else {
                return this.desc
            }
        },

        hoverImage() {
            console.log(this.images);
            let length = this.images.length;
            
            if(length >= 1 ){
                let i = Math.floor(Math.random() * (length + 1));
                return this.images[i];
            } else {
                return this.image;
            }
        }
    }
}
</script>

<style lang="scss">
    .slide {
        h4{
            font-size: 36px;
            margin: 12px;
        }
        p {
            font-size: 18px;
            margin: 12px;
        }
        img{
            width: 350px;
            max-height: 60%;
            margin: 12px;
        }
        height: 100%;
        width: 100%;
        flex-grow: 1;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        align-content: center;
        align-items: center;
        display: none;
    }

     @media (min-width: 320px) and (max-width: 720px) {
        .slide {
           h4 {
               font-size: 24px;
               margin: 12px;
           }
           .image {
                img {
                    width: 90%;
                    height: 100%;
                    object-fit: cover;
                }
               overflow: hidden;
               width: 100%;
               height: auto;
           }
           p {
               font-size: 13px;
           }
           
        }
    }
</style>