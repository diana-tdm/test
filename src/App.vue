<template>
  <TimerBlock v-for="n in this.count" v-bind:key="n" />
  <TimerAdd @add="add" />
</template>

<script>
import TimerBlock from "./components/Timer.vue";
import TimerAdd from "./components/TimerAdd.vue";

export default {
  name: "App",
  components: {
    TimerBlock,
    TimerAdd,
  },
  data() {
    return {
      count: 3,
    };
  },
  methods: {
    add() {
      this.count++;
    },
  },
};
</script>

<style>
body {
  width: 100vw;
  height: 100vh;
  margin: 0px;
  padding: 0px;
  background: #353638;
  --main-color: #9e9e9e;
  overflow: hidden auto;
}

#app {
  width: 775px;
  display: flex;
  row-gap: 45px;
  column-gap: 50px;
  flex-wrap: wrap;
  margin: 0px auto;
  padding: 72px 0px 82px;
}

@media (max-width: 874px) {
  #app {
    width: 500px;
  }
}

@media (max-width: 599px) {
  #app {
    width: 225px;
  }
}
</style>
