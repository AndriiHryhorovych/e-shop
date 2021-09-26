<template>
    <div class="header d-flex align-items-center">
        <div class="container">
            <div class="row d-flex align-items-center">
                <div class="col-2 title">
                    <router-link to="/" class="title-link">eShop</router-link>
                </div>
                <div class="col-4 d-flex search">
                    <b-nav-form form-class="d-flex">
                        <b-form-input size="sm" class="mr-sm-2" placeholder="Пошук"></b-form-input>
                        <b-button size="sm" class="my-2 my-sm-0 search-button" type="submit">Шукати</b-button>
                    </b-nav-form>
                </div>
                <div class="col-4 col-6">
                    <ul class="menu d-flex justify-content-end align-items-center">
                        <li>
                            <router-link to="/catalog/all" class="menu-item">Каталог</router-link>
                        </li>
                        <li>
                            <router-link to="/payments" class="menu-item">Оплата</router-link>
                        </li>
                        <li>
                            <router-link to="/delivery" class="menu-item">Доставка</router-link>
                        </li>
                        <li>
                            <router-link to="/cart" class="menu-item d-flex">      
                                <img src="@/assets/fluent_cart.png" alt="">
                                <cartCounter />  
                            </router-link>
                        </li>
                    </ul>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import cartCounter from "@/components/CartCounter.vue";
    export default {
        components: {
            cartCounter,
        }
    }
</script>

<style lang="scss" scoped>
.header {
    background-color: black;
    color: white;
    height: 60px;
    position: fixed;
    left: 0;
    top: 0;
    width: 100vw;
    z-index: 200;
}
.title-link {
    text-decoration: none;
    font-size: 32px;
    color: white;
    transition: 0.3s;
}
.title-link:hover {
    color: gray;
    transition: 0.3s;
}
.menu a{
    text-decoration: none;
    color: white;
    font-size: 16px;
    transition: 0.3s;
    margin: 0 15px;
}
.menu a:hover{
    color: gray;
    transition: 0.3s;
    img {
        transform: scale(1.2);
        transition: 0.3s;
    
    }
    
}
.menu li{
    display: flex;
    align-items: center;
}
.menu{
     margin: 0 0;
     padding: 0 16px;
}
.search {
 list-style-type: none;
}
.search-button {
    background-color: #ff842c;
    margin: 0 0 0 -5px;
    border-color: #ff842c;
    border-bottom-left-radius: 0;
    border-top-left-radius: 0;
}
</style>