<template>
    <div class="header d-flex align-items-center">
        <div class="container">
            <div class="row">
                <div class="col-2 title">
                    <router-link to="/" class="title-link">eShop</router-link>
                </div>
                <div class="col-4">

                </div>
                <div class="col-6">
                    <ul class="menu d-flex justify-content-between align-items-center">
                        <li>
                            <router-link to="/catalog" class="menu-item">Каталог</router-link>
                        </li>
                        <li>
                            <router-link to="/payments" class="menu-item">Оплата</router-link>
                        </li>
                        <li>
                            <router-link to="/delivery" class="menu-item">Доставка</router-link>
                        </li>
                        <li>
                            <router-link to="/cart" class="menu-item">Корзина</router-link>
                        </li>
                    </ul>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        
    }
</script>

<style lang="scss" scoped>
.header {
    background-color: black;
    color: white;
    height: 60px;
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
}
.menu a:hover{
    color: gray;
    transition: 0.3s;
    
}
.menu li{
    display: flex;
    align-items: center;
}
.menu{
     margin: 0 0;
     padding: 0 16px;
}
</style>