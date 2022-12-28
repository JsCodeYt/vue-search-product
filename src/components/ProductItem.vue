<template>
    <div class="product__item" v-for="product in products">
        <img :src="product.images[slideNumber].src || product.images[0]" alt="">
        <span class="product__author">{{ product.author }}</span>
        <div class="product__item-info">
            <div class="product__slider">
                <div class="slider__item" v-for="image in product.images">
                    <img :src="image.src || image" alt="">
                </div>
            </div>
            <h3>{{ product.name }}</h3>
            <span>{{ product.price }}</span>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            slideNumber: 0
        }
    },
    props: {
        products: {
            type: Array,
            required: true,
        }
    },
}
</script>
<style lang="scss">
.product__item {
    width: 240px;
    height: 400px;
    position: relative;
    border: 1px solid #000;
    padding: 10px;
    border-radius: 10px;

    img {
        height: 50%;
        width: 100%;
        object-fit: contain;
        z-index: 0;
    }

    .product__author {
        top: 5px;
        left: 2px;
        font-size: 12px;
        position: absolute;
        padding: 5px;
        background-color: #232323;
        color: white;
        border-radius: 10px;
        cursor: pointer;
    }

    .product__item-info {
        display: flex;
        flex-direction: column;
        gap: 1rem;

        h3 {
            font-size: 16px;
            font-weight: 300;
        }

        span {
            font-weight: 600;
        }

        .product__slider {
            padding: 10px;
            display: flex;
            align-items: center;
            gap: 10px;
            position: relative;
            overflow: hidden;

            .slider__item {
                border: 1px solid #000;
                height: 50px;
                width: 100px;
                cursor: pointer;
                position: relative;
                padding: 4px;
                border-radius: 10px;

                img {
                    height: 100%;
                    width: 100%;
                    object-fit: contain;
                }
            }
        }
    }
}
</style>