<template>
    <div class="single">
        <div class="single__imgs">
            <img class="single__img" :src="productInfo[0].images[sliderNumber].src || productInfo[0].images[0]" alt="">
            <div class="single__slider" v-for="image in productInfo[0].images">
                <img :src="image.src || productInfo[0].images[0]" alt="" @click="incre(image.id || 0)">
            </div>
            <p>{{ productInfo[0].name }}</p>
            <div class="product__comments">
                <div class="comment__write">
                    <input type="text" placeholder="write comment" @change="comment = $event.target.value">
                    <button @click="sendComment(comment)">Send</button>
                </div>
                <div class="comments">
                    <div class="comment__item" v-for="comment in productInfo[0].comments">
                        <span>{{ comment.comment }}</span>
                    </div>
                </div>
            </div>
        </div>
        <div class="single__info">
            <h1>Maxsulot haqida</h1>
            <ul class="info__items">
                <li class="single__item">
                    <h2>Brend</h2>
                    <span>{{ productInfo[0].author }}</span>
                </li>
                <li class="single__item">
                    <h2>Os turi</h2>
                    <span>{{ productInfo[0].OS }}</span>
                </li>
                <li class="single__item">
                    <h2>Diogonal</h2>
                    <span>{{ productInfo[0].diogonal }}</span>
                </li>
                <li class="single__item">
                    <h2>Ekran turi</h2>
                    <span>{{ productInfo[0].ekran }}</span>
                </li>
                <li class="single__item">
                    <h2>photo cam</h2>
                    <span>{{ productInfo[0].photocam }}</span>
                </li>
            </ul>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            sliderNumber: 0,
            comment: ""
        }
    },
    props: {
        productInfo: {
            type: Object,
            required: true,
        }
    },
    methods: {
        incre(itemId) {
            this.sliderNumber = itemId
        },
        sendComment(comment) {
            this.$emit("comment", comment)
        }
    }
}
</script>
<style lang="scss">
.single {
    display: flex;
    gap: 3rem;

    .single__imgs {
        width: 50%;

        .single__img {
            height: 500px;
            width: 100%;
            object-fit: contain;
        }

        .single__slider {
            display: inline-block;
            margin-right: 20px;

            img {
                width: 80px;
                height: 80px;
                object-fit: contain;
                padding: 5px;
                border: 1px solid #000;
                border-radius: 10px;
                cursor: pointer;
            }
        }

        .comment__write {
            input {
                border: none;
                outline: none;
                width: 350px;
                margin: 20px 0px;
                font-size: 17px;
            }

            button {
                border: none;
                padding: 10px;
                outline: none;
            }
        }
    }

    .single__info {
        width: 50%;

        .info__items {
            list-style: none;

            .single__item {
                display: flex;
                align-items: center;
                gap: 1rem;

                h2 {
                    font-size: 23px;
                }

                span {
                    font-size: 16px;
                    font-weight: 600;
                }
            }
        }
    }
}
</style>