<template>
     <div class="outFirst">
        <div class="container">
            <div class="container bg-pink">
                <div class="overlay">
                    <img src="../assets/bg-pattern.svg" id="overlayPattern" />
                </div>
                <div class="card">
                    <div class="item-container">
                        <div class="item-photo">
                            <img :src="api.image" id="item-photo" />
                        </div>
                        <div class="item-desc">
                            <h1 class="font-magenta title">{{ api.title }}</h1>
                            <div class="sub-title">
                                <span>{{ api.category }}</span>
                                <div class="rating">
                                    <span>{{ api.rating.rate }}</span>
                                    <span class="bg-magenta circle"></span>
                                    <span class="bg-magenta circle"></span>
                                    <span class="bg-magenta circle"></span>
                                    <span class="bg-magenta circle"></span>
                                    <span class="bg-magenta circle"></span>
                                </div>
                            </div>
                            <div class="desc">
                                <p>{{ api.description }}</p>
                            </div>
                            <div class="item-info">
                                <hr>
                                <br>
                                <span class="font-magenta price">${{ api.price }}</span>
                                <div class="buttonFlex">
                                    <button class="bg-magenta cta-buy">Buy Now</button>
                                    <button @click="nextCta" class="border-magenta font-magenta cta-next">Next Product</button>
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
        name: 'WomenSection',
        props: ["api"],
        methods: {
            nextCta() {
                this.$emit('next-button');
            }
        }
    }
</script>

<style scoped>
</style>