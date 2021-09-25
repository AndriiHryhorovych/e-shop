<template>
    <div class="cart-empty">
        <div class="container">
            <div class="row">
                <div class="col-12 d-flex flex-column justify-content-center align-items-center">
                    <div class="cart-title">
                        Кошик замовлень
                    </div>
                    <div class="cart-info">
                        На жаль, Ви ще нічого не додали до кошика
                    </div>
                    <div id="button-to-catalog">
                        <b-button href="/catalog/all">До каталогу</b-button>
                    </div>   
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
.cart-empty {
    min-height: calc(100vh - 151px);
    .cart-title{
        margin: 41px 0 23px 0;
        font-family: Roboto;
        font-size: 36px;
        font-weight: 500;
        font-stretch: normal;
        font-style: normal;
        line-height: normal;
        letter-spacing: normal;
        text-align: center;
        color: #000;
    }
    .cart-info {
        width: 542px;
        height: 54px;
        flex-grow: 0;
        margin: 23px 0 33px 0;
        padding: 12px 0 16px;
        border-radius: 6px;
        background-color: rgba(255, 168, 0, 0.21);
        font-family: Roboto;
        font-size: 22px;
        font-weight: 500;
        font-stretch: normal;
        font-style: normal;
        line-height: normal;
        letter-spacing: normal;
        text-align: center;
        color: #ff842c;
    }
    .btn {
        height: 56px;
        width: 178px;
        flex-grow: 0;
        margin: 33px 0;
        padding: 15px 0;
        border-radius: 6px;
        border-color: #ff842c;
        box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.15);
        background-color: #ff842c;
        font-family: Roboto;
        font-size: 22px;
        font-weight: 500;
        font-stretch: normal;
        font-style: normal;
        line-height: normal;
        letter-spacing: normal;
        text-align: center;
        color: #fff;
    }
    
}
.button-to-catalog {
    text-align: center;
    
    
}
</style>