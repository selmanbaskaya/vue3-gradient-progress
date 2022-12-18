<script setup>
import { reactive, ref } from "vue"

const btnLabel = ref("Start")
const style = reactive({
  opacity: 0,
  display: "none",
  height: ''
})

function startProgress() {
  btnLabel.value = "Stop"

  style.opacity = 1
  style.display = "block"
  style.height = "20px"
}

function finishProgress() {
  btnLabel.value = "Start"

  style.opacity = 0
  style.display = "none"
  style.height = ""
}
</script>

<template>
  <div class="progress" :style="style"></div>

  <button
    class="btn"
    :class="btnLabel === 'Start' ? 'startBtn' : 'stopBtn'"
    @click="btnLabel === 'Start' ? startProgress() : finishProgress()"
  >
    {{ btnLabel }}
  </button>
</template>

<style scoped>
.progress {
  background: #a307ba;
  background: #27c4f5 -webkit-gradient(linear, left top, right top, from(#27c4f5), color-stop(#a307ba), color-stop(#fd8d32), color-stop(#70c050), to(#27c4f5));
  background: #27c4f5 -webkit-linear-gradient(left, #27c4f5, #a307ba, #fd8d32, #70c050, #27c4f5);
  background: #27c4f5
    linear-gradient(to right, #27c4f5, #a307ba, #fd8d32, #70c050, #27c4f5);
  -webkit-animation: 2s linear infinite rainbow, 0.5s ease-out enter;
  animation: 2s linear infinite rainbow, 0.5s ease-out enter;
  -webkit-transition: opacity 0.2s ease-in-out;
  transition: opacity 0.2s ease-in-out;
  -webkit-transform-origin: left;
  transform-origin: left;
  background-size: 500%;
  z-index: 999999;
  position: fixed;
  display: block;
  width: 100%;
  opacity: 1;
  left: 0;
  top: 0;
}
@-webkit-keyframes rainbow {
  0% {
    background-position: 0% 0;
  }
  to {
    background-position: 125% 0;
  }
}
@keyframes rainbow {
  0% {
    background-position: 0% 0;
  }
  to {
    background-position: 125% 0;
  }
}
@-webkit-keyframes enter {
  0% {
    -webkit-transform: scaleX(0);
    transform: scaleX(0);
  }
  to {
    -webkit-transform: scaleX(1);
    transform: scaleX(1);
  }
}
@keyframes enter {
  0% {
    -webkit-transform: scaleX(0);
    transform: scaleX(0);
  }
  to {
    -webkit-transform: scaleX(1);
    transform: scaleX(1);
  }
}

.btn {
  position: fixed;
  top: 50%;
  left: 50%;
  padding: 10px 50px;
  font-size: 24px;
  color: white;
  border-radius: 10px;
  border-color: #eee;
  border-style: solid;
  transition: 0.5s;
  background-size: 200% auto;
}

.startBtn {
  background-image: linear-gradient(to right, #84fab0 0%, #8fd3f4 51%, #84fab0 100%);
}

.stopBtn {
  background-image: linear-gradient(to right, #fbc2eb 0%, #a6c1ee 51%, #fbc2eb 100%);
}

.btn:hover {
  background-position: right center;
}
</style>
