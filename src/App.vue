<template> 
<div id="app">
    <div class ="header-menu"><NavBar 
      @show-home="ShowHome"
      @show-location="ShowLocation"
      @show-menu="ShowMenu"
      @show-vegan="ShowVegan"
      @show-about="ShowAbout"
      @show-contact="ShowContact"
      @toggle-vegan-on="ToggleVeganOn"
      @toggle-vegan-off="ToggleVeganOff"
      /></div>
      <h1 class="juice" v-show="MenuExists==='yes' && veganOnly === false">Full Menu</h1>
      <h1 class="juice"  v-show="MenuExists==='yes' && veganOnly === true">Vegan Menu</h1>
    <div class="main" v-show="HomeExists === 'yes'"><MainPage @show-menu="ShowMenu"/></div>
    <div class="main" v-show="LocationExists === 'yes'"><LocationPage/></div>
    <div class="main" v-show="MenuExists === 'yes'"><MenuPage :veganOnly="veganOnly"/></div>
    <div class="main" v-show="VeganExists === 'yes'"><VeganPage @show-home="ShowHome" @toggle-vegan-on="ToggleVeganOn" @show-menu="ShowMenu" /></div>
    <div class="main" v-show="AboutExists === 'yes'"><AboutPage/></div>
    <div class="main" v-show="ContactExists === 'yes'"><ContactPage/></div>
    <div><FooterBar/></div>
</div>
</template>

<script>
import NavBar from './components/NavBar.vue'
import LocationPage from './components/LocationPage.vue'
import MainPage from './components/MainPage.vue'
import FooterBar from './components/FooterBar.vue'
import VeganPage from './components/VeganPage.vue'
import AboutPage from './components/AboutPage.vue'
import ContactPage from './components/ContactPage.vue'
import MenuPage from './components/MenuPage.vue'

export default {
  name: 'App',
  components: {
    NavBar,
    LocationPage,
    MainPage,
    FooterBar,
    VeganPage,
    AboutPage,
    ContactPage,
    MenuPage,
  },
  data(){
    return {
      veganOnly: false,
      HomeExists: 'yes',
      LocationExists: 'no',
      VeganExists: 'no',
      AboutExists: 'no',
      ContactExists: 'no',
      MenuExists: 'no',
    }
  },

  methods: {
    ToggleVeganOn() {
      this.veganOnly = true
    },
    ToggleVeganOff() {
      this.veganOnly = false
    },
     ShowHome() {
      this.HomeExists =  'yes',
      this.LocationExists = 'no'
      this.VeganExists = 'no'
      this.AboutExists = 'no'
      this.ContactExists = 'no'
      this.MenuExists = 'no'
     },
     ShowLocation() {
      this.HomeExists =  'no',
      this.LocationExists = 'yes'
      this.VeganExists = 'no'
      this.AboutExists = 'no'
      this.ContactExists = 'no'
      this.MenuExists = 'no'
     },
     ShowVegan() {
      this.HomeExists =  'no',
      this.LocationExists = 'no'
      this.VeganExists = 'yes'
      this.AboutExists = 'no'
      this.ContactExists = 'no'
      this.MenuExists = 'no'
     },
     ShowAbout() {
      this.HomeExists =  'no',
      this.LocationExists = 'no'
      this.VeganExists = 'no'
      this.AboutExists = 'yes'
      this.ContactExists = 'no'
      this.MenuExists = 'no'
     },
     ShowContact() {
      this.HomeExists =  'no',
      this.LocationExists = 'no'
      this.VeganExists = 'no'
      this.AboutExists = 'no'
      this.ContactExists = 'yes'
      this.MenuExists = 'no'
     },
     ShowMenu() {
      this.HomeExists =  'no',
      this.LocationExists = 'no'
      this.VeganExists = 'no'
      this.AboutExists = 'no'
      this.ContactExists = 'no'
      this.MenuExists = 'yes'
     },
  }
 
}
</script>


<style>

@font-face {
    font-family: 'juice';
    src: local('juice'),
    url(./fonts/juice.ttf);
}
@media (max-width: 991.5px) {
  .header-menu {
    font-size: .75em;
  }
}

@media (max-width: 1685.5px) and (min-width: 991.5px) {
  .header-menu {
    font-size: .75em;
  }
  }

  @import url('https://fonts.googleapis.com/css2?family=Amatic+SC:wght@700&family=Oswald&display=swap');

#app {
  font-family: 'Oswald', sans-serif;
  font-size: 1.5em;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
  margin-top: 60px;
  display:flex;
  flex-direction: column;
}

@media only screen {
  #app {
    font-size: 1.15em;
 }
}
.main {
  display: flex;
  justify-content: center;
}

.juice {
  font-family: juice;
  font-size: 2em;
  color: #FFFAA1;
}
</style>
