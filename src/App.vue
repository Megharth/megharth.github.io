<template>
  <div id="app">
    <!--TODO: ADD Comments-->
    <div class="menu" @click="open = !open">
      <div><img src="./assets/menu.png" alt="menu" class="img-fluid"></div>
    </div>
    <transition name="open">
      <navbarComponent v-if="open" @changepage="changePage($event)"></navbarComponent>
    </transition>
    <mainComponent v-if="pageNo === 0"></mainComponent>
    <skillComponent v-if="pageNo === 1"></skillComponent>
    <educationComponent v-if="pageNo === 2"></educationComponent>
    <projectsComponent v-if="pageNo === 3"></projectsComponent>
    <contactComponent v-if="pageNo === 4"></contactComponent>
    <div class="navigator">
      <div class="prev-btn" v-if="pageNo>0">
        <img src="./assets/larrow.png" class="img-fluid" alt="prev" @click="pageNo = pageNo - 1">
      </div>
      <div class="next-btn" v-if="pageNo< pages-1">
        <img src="./assets/rarrow.png" class="img-fluid" alt="next" @click="pageNo = pageNo + 1">
      </div>
    </div>
  </div>
</template>

<script>
import navbarComponent from './components/navbarComponent'
import mainComponent from './components/mainComponent'
import skillComponent from './components/skillComponent'
import educationComponent from './components/educationComponent'
import projectsComponent from './components/projectsComponent'
import contactComponent from './components/contactComponent'

export default {
  name: 'app',
  components: {
    navbarComponent,
    mainComponent,
    skillComponent,
    educationComponent,
    projectsComponent,
    contactComponent
  },
  data() {
    return {
      open: false,
      pages: 5,
      pageNo: 0
    }
  },
  methods: {
    changePage($event) {
      this.pageNo = $event
      this.open = false
    }
  }
}
</script>

<style lang="sass">
@import url('https://fonts.googleapis.com/css?family=Permanent+Marker|Exo+2|Staatliches')
@import "./sass/app"
</style>
