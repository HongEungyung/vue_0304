<script setup>
import {ref} from "vue"
const products = ["아이폰", "갤럭시", "맥북"]
const cart = ref([])
const addToCart = (product)=>{
cart.value.push(product)
}
</script>
<template>
    <h2>상품 목록</h2>
    <ul>
    <li v-for="product in products" :key="product">{{ product }}
    <!-- product는 아무것도 아님. 중요한 건 in products -->
    <button @click="addToCart(product)">추가</button>
    </li>
    </ul>
    <h2>장바구니</h2>
    <ul>
    <li v-for="item in cart" :key="item">{{ item }}</li>
    <!-- 여기도 마찬가지 중요한건 in cart. -->
    </ul>
</template>
<style scoped>

</style>
