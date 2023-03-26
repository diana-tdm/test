<template>
  <div class="timer-add">
    <button @click="$emit('add')" class="timer-add__btn"></button>
  </div>
</template>

<script>
export default {
  name: "TimerAdd",
};
</script>

<style>
.timer-add {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 225px;
  height: 120px;
  background: #696969;
  color: var(--main-color);
}

.timer-add__btn {
  position: relative;
  width: 100%;
  height: 100%;
  appearance: none;
  border: none;
  padding: 0px;
  cursor: pointer;
  background: none;
}

.timer-add__btn:hover {
  --main-color: #ffffff;
}

.timer-add__btn::after {
  position: absolute;
  content: "";
  width: 22px;
  height: 4px;
  background-color: var(--main-color);
  left: calc(50% - 11px);
  top: calc(50% - 2px);
}

.timer-add__btn::before {
  position: absolute;
  content: "";
  width: 4px;
  height: 22px;
  background-color: var(--main-color);
  left: calc(50% - 2px);
  top: calc(50% - 11px);
}
</style>
