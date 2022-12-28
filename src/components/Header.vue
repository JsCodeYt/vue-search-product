<template>
    <header class="header" id="header">
        <form class="header__form" @submit.prevent>
            <input type="text" placeholder="search" @input="search = $event.target.value" class="header__input">
            <button class="header__btn" @click="handleSend(search)">
                <i class="fa-solid fa-magnifying-glass"></i>
            </button>
        </form>
    </header>
</template>
<script>
export default {
    data() {
        return {
            search: ""
        }
    },
    methods: {
        handleSend(item) {
            this.$emit("handleSend", item)
        }
    }
}
</script>
<style>
.header__form {
    display: flex;
    align-items: center;
    gap: 1rem;
}

.header__btn {
    background-color: #fff;
    border: none;
    outline: none;
}

.header__input {
    height: 34px;
    width: 300px;
    padding: 0px 10px;
    font-size: 20px;
    border-radius: 5px;
    outline: none;
}

.header__btn i {
    font-size: 20px;
    color: pointer;
}
</style>