<template>
    <div>
        <div v-if="count == 1" class="pos-rel">
            <div class="cart d-flex align-items-center justify-content-center">
                {{count}}
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data(){
            return{
                count:0,
            };
        },
        methods:{
            checkItems(){
                var items = window.localStorage.getItem('cart');
                if (items){
                    this.count = 1;
                }
                console.log(items);
            },
        },
        mounted(){
            setInterval(() =>{
                this.checkItems();
            }, 300)
        }
    }
</script>

<style lang="scss" scoped>
.cart{
    width: 20px;
    height: 20px;
    border-radius: 50%;
    background-color: red;
    font-family: Roboto;
    font-size: 16px;
    font-weight: 500;
    font-stretch: normal;
    font-style: normal;
    line-height: normal;
    letter-spacing: normal;
    text-align: left;
    color: #fff;
    position: absolute;
    top: -5px;
    right: -10px;
}
.pos-rel {
    position: relative;
}

</style>