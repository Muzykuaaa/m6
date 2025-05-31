<script setup>
import { ref } from "vue";

let src = ref("");
let brand = ref("");
let price = ref("");
let size = ref("");
let rating = ref("");
let description = ref("");

function sendItem() {
    let data = {
        "src": src.value,
        "brand": brand.value,
        "price": price.value,
        "size": size.value,
        "rating": rating.value,
        "description": description.value,
    }
    fetch("https://ae51c2d080f15e19.mokky.dev/product", 
    {
        method:"POST",
        headers: {'Content-Type': "application/json" },
        body: JSON.stringify(data),
    }
        
    )
    src.value = "";
    brand.value = "";
    price.value = "";
    size.value = "";
    rating.value = "";
    description.value = "";
}

</script>

<template>
    <form @submit.prevent="sendItem">
        <label>
            <p>Введите ссылку на картинку:</p>
            <input v-model="src" required/>
            <img v-if="src" :src="src" />
        </label>

        <label>
            <p>Введите название:</p>
            <input v-model="brand" required/>
        </label>    

        <label>
            <p>Введите цену:</p>
            <input v-model="price" required/>
        </label>    
        
        <label>
            <p>Введите размер:</p>
            <input v-model="size" required/>
        </label>    

        <label>
            <p>Введите рейтинг:</p>
            <input v-model="rating" required/>
        </label>  

        <label>
            <p>Введите описание товара:</p>
            <input v-model="description" required/>
        </label>      

    <button class="btn" type="submit"> Сохранить </button>

    </form>


</template>

<style scoped>
input{
    font-size: 13px;
    border: 1px solid #cecece;
    border-radius: 8px;
    width: 200px;
    padding: 3px;
    background: #f6f6f6;
    outline: none;
}
img{
    display: flex;
    width: 150px;
}
*{
    margin: 5px;
}
.btn{
    border: none;
    border-radius: 5px;
    text-decoration: none;
    color: white;
    background: #0b63f6;
    box-shadow: 0 5px 0 #003cc5;
    margin-left: 10px;
    padding: 8px;
}

.btn:hover{
    background: #003cc5;
    box-shadow: none;
    position: relative;
    top: 5px;
}
</style>