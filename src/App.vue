<template>
  <div id="app">
  <div v-if="isLoading" class="loading">
    <span class="loader"></span>
  </div>
  <div v-if="!isLoading">
    <div v-if="mens">
      <ManSection v-bind:api="api" @next-button="nextButton"/>
    </div>
    <div v-if="women">
          <WomenSection v-bind:api="api" @next-button="nextButton"/>
    </div>
    <div v-if="unavaible">
          <UnavailPage @next-button="nextButton"/>
    </div>
  </div>
  </div>
</template>

<script>
import axios from 'axios'
import ManSection from './components/ManSection'
import WomenSection from './components/WomenSection'
import UnavailPage from './components/Unavail'

export default {
  name: 'App',
  components: {
    ManSection,
    WomenSection,
    UnavailPage,
  },
  data() {
    return {
      api: [],
      mens: false,
      women: false,
      unavaible: false,
      curr: 1,
      isLoading: false,
    }
  },
  methods: {
    nextButton() {
      this.isLoading = true;
      this.curr++;
      if (this.curr > 20) {
    this.curr = 1;
  }
      axios.get(`https://fakestoreapi.com/products/${this.curr}`)
      .then((res) => {
        this.api = res.data
        res.data.category === "men's clothing" ? this.mens = true : this.mens = false;
        res.data.category === "women's clothing" ? this.women = true : this.women = false;
        res.data.category === "jewelery" || res.data.category === "electronics" ? this.unavaible = true : this.unavaible = false;
        this.isLoading = false;
      })
      .catch(err => console.log(err))
    }
  },
  created() {
    this.isLoading = true;
    axios.get('https://fakestoreapi.com/products/1')
    .then((res) => {
      this.api = res.data
        res.data.category === "men's clothing" ? this.mens = true : this.mens = false;
        res.data.category === "women's clothing" ? this.women = true : this.women = false;
        res.data.category === "jewelery" || res.data.category === "electronics" ? this.unavaible = true : this.unavaible = false;
      this.isLoading = false;
    })
    .catch(err => console.log(err))
  }
}
</script>

<style>
:root {
    --navy: #002772;
    --pink: #fde2ff;
    --black: #1e1e1e;
    --magenta: #720060;
    --blue: #d6e6ff;
    --dark-gray: #3f3f3f;
    --gray: #dcdcdc;
    --white: #fff;
}

* {
    margin: 0%;
    box-sizing: border-box;
    font-family: 'Inter', sans-serif;
}
.loading {
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
.loader {
  border: 16px solid var(--blue);
  border-radius: 50%;
  border-top: 16px solid var(--white);
  border-bottom: 16px solid var(--pink);
  width: 120px;
  height: 120px;
  -webkit-animation: spin 2s linear infinite;
  animation: spin 2s linear infinite;
}

@-webkit-keyframes spin {
  0% { -webkit-transform: rotate(0deg); }
  100% { -webkit-transform: rotate(360deg); }
}

@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
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

.bg-blue {
    background: linear-gradient(180deg, var(--blue) 65%, var(--white) 50%);
}
.bg-pink {
  background: linear-gradient(180deg, var(--pink) 65%, var(--white) 50%);
}

.overlay {
    position: absolute;
    width: 100%;
    height: 100%;
    top: -60%;
    z-index: 1;
    overflow: hidden;
}

.overlay .img {
    width: 100%;
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

.item-container {
    display: flex;
    position: relative;
    width: 100%;
    height: 100%;
    box-sizing: border-box;
}

.item-photo {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 40%;
}

#item-photo {
    max-width: 70%;
}

.item-desc {
    display: flex;
    width: 80%;
    font-size: 8px;
    margin-right: 5%;
    flex-direction: column;
    justify-content: space-between;
}

.font-navy {
    color: var(--navy);
}
.font-pink {
  color: var(--pink);
}

.bg-gray {
    background: linear-gradient(180deg, var(--gray) 65%, var(--white) 50%);
}

.bg-magenta {
  background: var(--magenta);
}

.font-magenta {
  color: var(--magenta);
}

.bg-navy {
    background: var(--navy);
}

.border-navy {
    border: 2px solid var(--navy);
}

.border-magenta {
  border: 2px solid var(--magenta);
}

.title {
    font-size: 32px;
    font-weight: 600;
    margin: 0%;
    padding-bottom: 5%;
}

.sub-title {
    position: relative;
    display: flex;
    width: 100%;
    justify-content: space-between;
    top: -10%;
    font-size: 24px;
    color: var(--dark-gray);
    border-bottom: 1px solid var(--gray);
}

.rating {
    display: flex;
    gap: 3px;
    align-items: center;
}

.circle {
    display: block;
    width: 14px;
    height: 14px;
    border-radius: 100%;
}

.desc {
    color: var(--gray);
    position: relative;
    width: 100%;
    font-size: 14px;
    top: -20%;
    color: var(--black);
    margin-top: 10%;
}

.price {
    font-size: 32px;
    font-weight: 600;
    margin-top: 5%;
}

.buttonFlex {
    display: flex;
    margin-top: 16px;
    width: 100%;
    display: flex;
    gap: 12px;
}

.cta-buy {
    width: 35%;
    height: 36px;
    font-size: 16px;
    border-radius: none;
    font-weight: 700;
    cursor: pointer;
    color: white;
}

.cta-next {
    width: 35%;
    height: 36px;
    font-size: 16px;
    border-radius: none;
    font-weight: 700;
    cursor: pointer;
}

.item-info {
    margin-bottom: 5%;
}
</style>
