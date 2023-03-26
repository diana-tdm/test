<template>
  <div class="timer" :class="{ 'timer--started': started }">
    <div class="timer__counter">
      {{ this.timeString }}
    </div>
    <div class="timer__btns">
      <button
        v-if="!started"
        @click="start"
        class="timer__btn timer__btn--play"
      ></button>
      <button
        v-else
        @click="pause"
        class="timer__btn timer__btn--pause"
      ></button>
      <button @click="stop" class="timer__btn timer__btn--stop"></button>
    </div>
  </div>
</template>

<script>
export default {
  name: "TimerBlock",
  data() {
    return {
      time: 0,
      started: false,
    };
  },
  mounted() {
    setTimeout(this.countdown, 1000);
    this.startTime = Date.parse(new Date());
  },
  computed: {
    timeString() {
      const seconds = this.time % 60;
      const minutes = Math.floor(this.time / 60) % 60;
      const hours = Math.floor(this.time / 60 / 60);
      const secondsString = ("" + seconds).padStart(2, "0");
      const minutesString = ("" + minutes).padStart(2, "0");
      let time = seconds;
      if (hours > 0) {
        time = hours + ":" + minutesString + ":" + secondsString;
      } else {
        if (minutes > 0) {
          time = minutes + ":" + secondsString;
        }
      }
      return time;
    },
  },
  methods: {
    start() {
      this.started = true;
    },
    pause() {
      this.started = false;
    },
    stop() {
      this.started = false;
      this.time = 0;
    },
    countdown() {
      if (this.started) {
        this.time++;
      }
      setTimeout(this.countdown, 1000);
    },
  },
};
</script>

<style>
.timer {
  width: 225px;
  height: 120px;
  background: #696969;
  font-family: "Arial";
  font-weight: 400;
  font-size: 22px;
  line-height: 21px;
  text-align: center;
  color: var(--main-color);
}

.timer--started {
  --main-color: #ffffff;
}

.timer__counter {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 60px;
  border-bottom: 1px solid var(--main-color);
}

.timer__btns {
  height: 60px;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 48px;
}

.timer__btn {
  width: 20px;
  height: 20px;
  background: var(--main-color);
  appearance: none;
  border: none;
  padding: 0px;
  cursor: pointer;
}

.timer__btn:hover {
  --main-color: #ffffff;
}

.timer__btn--play {
  width: 0;
  height: 0;
  border-style: solid;
  border-width: 10px 0 10px 17px;
  border-color: transparent transparent transparent var(--main-color);
  background: none;
}

.timer__btn--pause {
  width: 10px;
  background: none;
  border-left: 3px solid var(--main-color);
  border-right: 3px solid var(--main-color);
}
</style>
