<template>
    <div class="header d-flex align-items-center">
        <div class="container">
            <div class="row">
                <div class="col-2 title">
                    <router-link to="/">eShop</router-link>
                </div>
                <div class="col-4">

                </div>
                <div class="col-6">
                    <ul class="menu d-flex justify-content-between">
                        <li>
                            <router-link to="/catalog">Каталог</router-link>
                        </li>
                        <li>
                            <router-link to="/payments">Оплата</router-link>
                        </li>
                        <li>
                            <router-link to="/delivery">Доставка</router-link>
                        </li>
                        <li>
                            <router-link to="/cart">Корзина</router-link>
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
.title {
    font-size: 28px;
}
</style>