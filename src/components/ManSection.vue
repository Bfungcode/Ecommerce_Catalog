<template>
     <div class="outFirst">
        <div class="container">
            <div class="container bg-blue">
                <div class="overlay">
                    <img src="../assets/bg-pattern.svg" id="overlayPattern" />
                </div>
                <div class="card">
                    <div class="item-container">
                        <div class="item-photo">
                            <img :src="api.image" id="item-photo" />
                        </div>
                        <div class="item-desc">
                            <h1 class="font-navy title">{{ api.title }}</h1>
                            <div class="sub-title">
                                <span>{{ api.category }}</span>
                                <div class="rating">
                                    <span>{{ api.rating.rate }}</span>
                                    <span class="bg-navy circle"></span>
                                    <span class="bg-navy circle"></span>
                                    <span class="bg-navy circle"></span>
                                    <span class="bg-navy circle"></span>
                                    <span class="bg-navy circle"></span>
                                </div>
                            </div>
                            <div class="desc">
                                <p>{{ api.description }}</p>
                            </div>
                            <div class="item-info">
                                <hr>
                                <br>
                                <span class="font-navy price">${{ api.price }}</span>
                                <div class="buttonFlex">
                                    <button class="bg-navy cta-buy">Buy Now</button>
                                    <button @click="nextCta" class="border-navy font-navy cta-next">Next Product</button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'ManSection',
        props:["api"],
        methods: {
            nextCta() {
                this.$emit('next-button');
            }
        }
    }
</script>

<style scoped>

</style>