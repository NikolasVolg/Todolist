<template>
    <div class="carousel">
        <slot>

        </slot>

        <button class="carousel__nav carousel__next" @click.prevent="next"></button>
        <button class="carousel__nav carousel__prev" @click.prevent="prev"></button>

        <div class="carousel__pagination">
            <button v-for="n in slidesCount" @click="goto(n-1)" :class="{active: n-1 == index}" :key="n.id"></button>
        </div>
    </div>
</template>

<script>



export default {
    data () {
        
        return {
            index: 0,
            slides: [],
            direction: 'right'
        }
    },

    computed: {
        slidesCount () {
            return this.slides.length
        }
    },

    watch: {
        slides (slides) {
            if (this.index >= this.slidesCount) {
                this.index = this.slidesCount -1
            }
        }
    },

    methods: {
        next () {
            this.index++
            this.direction = 'right'
            if (this.index >= this.slidesCount) {
                this.index = 0
            }
        },
        prev () {
            this.index--
            this.direction = 'left'
            if (this.index < 0) {
                this.index = this.slidesCount -1
            }
        },
        goto (index) {
            this.direction = index > this.index ? 'right' : 'left'
            this.index = index
        }
    },

     mounted () {
        this.slides = this.$children
    },
}
</script>

<style>
.carousel {
    position: relative;
    overflow: hidden;
}

.carousel__nav {
    position: absolute; 
    top: 50%;
    left: 1%;
    margin-top: -31px;
    background: url(prevIcon.jpg);
    width: 60px;
    height: 60px;
}

.carousel__nav.carousel__next {
    right: 10px;
    left: auto;
    background: url(nextIcon.jpg);
}

.carousel__pagination {
    position: absolute;
    bottom: 10px;
    left: 0;
    right: 0;
    text-align: center;
}

.carousel__pagination button {
    display: inline-block;
    width: 10px;
    height: 10px;
    background: #000;
    opacity: 0.8;
    border-radius: 10px;
    margin: 0 4px;
}

.carousel__pagination button.active {
    background-color: #fff;
}

</style>
