<template>
    <div class="outFirst">
        <div class="container">
            <div class="container bg-gray">
                <div class="card">
                    <div class="unavaible-container">
                        <div class="overlay">
                            <img src="../assets/sad-face.svg">
                        </div>
                        <div class="nextStep">
                            <p>This product is unavaible to show</p>
                            <button @click="nextCta" class="cta-next">Next Product</button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "UnavailPage",
    methods: {
            nextCta() {
                this.$emit('next-button');
            }
        }
}
</script>

<style scoped>
* {
    margin: 0%;
    box-sizing: border-box;
    font-family: 'Inter', sans-serif;
}

.outFirst {
    margin: 0;
    box-sizing: border-box;
}
.cta-next {
    width: 35%;
    height: 36px;
    font-size: 16px;
    border-radius: none;
    font-weight: 700;
    cursor: pointer;
}

.outFirst {
    margin: 0;
    box-sizing: border-box;
}

.container {
    position: relative;
    width: 100%;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
}

.overlay {
    display: flex;
    justify-content: center;
    align-items: center;
    position: absolute;
    z-index: 5;
    padding-left: 10%;
    width: 80%;
    margin-top: 25%;
}

.card {
    display: flex;
    position: relative;
    z-index: 2;
    width: 80%;
    height: 70vh;
    background-color: var(--white);
    border-radius: 10px;
    padding: 48px 32px;
    box-shadow: 0 4px 6px -1px rgb(0 0 0 / 10%), 0 2px 4px -2px rgb(0 0 0 / 10%);
}

.bg-gray {
    background: linear-gradient(180deg, var(--gray) 65%, var(--white) 50%);
}


.cta-next {
    width: 35%;
    height: 36px;
    font-size: 16px;
    border-radius: none;
    font-weight: 700;
    cursor: pointer;
    background: white;
}

.unavaible-container {
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}

.nextStep {
    text-align: center;
    width: 100%;
    z-index: 5;
}
</style>