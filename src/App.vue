<template>
  <div id="app" class="container" :class="{blue: isActive}" >
    <div class="row">
      <div class="col-12 pt-3 text-end">
        <span class="text-light" @click="changeColor" role="button">
          <i class="fa-solid fa-circle-half-stroke fa-2x"></i>
        </span>
      </div>
    </div>
    <Home />
  </div>
</template>

<script>
import Home from "./components/Home.vue";

export default {
  name: "App",
  components: {
    Home,
  },
  data() {
    return {
      isActive: false,
    };
  },
  methods: {
    changeColor() {
      console.log('click');

      if(this.isActive == false) {
        this.isActive = true;
      } else {
        this.isActive = false;
      }
    },
  },
};
</script>

<style lang="scss">
@import "./assets/scss/App.scss";
#app {
      height: 100vh;
}

#app.blue {
    background: blue;
    color: white;
  }
</style>
