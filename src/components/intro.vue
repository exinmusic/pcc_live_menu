<template>
	
<div class="animated-title">
  <div class="text-top">
    <div>
      <span>Connecting...</span>
      <span>with your mom.</span>
    </div>
  </div>
  <div class="text-bottom">
    <div>🖕Done!</div>
  </div>
</div>

</template>

<script>
export default {
  name: 'Intro'
  }
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css?family=Roboto:700");
@keyframes showTopText {
  0% {
    transform: translate3d(0, 100%, 0);
  }
  40%, 60% {
    transform: translate3d(0, 50%, 0);
  }
  100% {
    transform: translate3d(0, 0, 0);
  }
}
@keyframes showBottomText {
  0% {
    transform: translate3d(0, -100%, 0);
  }
  100% {
    transform: translate3d(0, 0, 0);
  }
}
.animated-title {
  color: #FF3377;
  font-family: Roboto, Arial, sans-serif;
  height: 90vmin;
  left: 50%;
  position: absolute;
  top: 50%;
  transform: translate(-50%, -50%);
  width: 90vmin;
}

.animated-title > div {
  height: 50%;
  overflow: hidden;
  position: absolute;
  width: 100%;
}

.animated-title > div div {
  font-size: 12vmin;
  padding: 2vmin 0;
  position: absolute;
}

.animated-title > div div span {
  display: block;
}

.animated-title > div.text-top {
  border-bottom: 1vmin solid yellow;
  top: 0;
}

.animated-title > div.text-top div {
  animation: showTopText 1s;
  animation-delay: 1s;
  animation-fill-mode: forwards;
  bottom: 0;
  transform: translate(0, 100%);
}

.animated-title > div.text-top div span:first-child {
  color: #00FF74;
}

.animated-title > div.text-bottom {
  bottom: 0;
}

.animated-title > div.text-bottom div {
  animation: showBottomText 1.5s;
  animation-delay: 2.5s;
  animation-fill-mode: forwards;
  top: 0;
  transform: translate(0, -100%);
}

body {
  background-color: #121212;
}

</style>