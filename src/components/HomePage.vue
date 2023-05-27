<template>
  <div class="home-page-wrapper">
    <ReadingSvg :height="450" :width="600" class="reading-svg"/>
    <div class="welcome-text">{{ text }}</div>
    <transition-group name="fade">
        <div v-if="!isTyping" class ="explore-button" @click="showIcons = !showIcons">Explore</div>
    </transition-group>
    <div class="icons-container">
        <a href="https://github.com/SwikritiT">
            <img class="icon" v-if="showIcons" src="./icons/github.svg" alt="Github icon"/>
        </a>
        <a href="https://www.linkedin.com/in/swikriti-tripathi/">
            <img class="icon" v-if="showIcons" src="./icons/linkedin.svg" alt="linkedIn icon"/>
        </a>
        <a href="https://www.instagram.com/greywaren934/">
            <img class="icon" v-if="showIcons" src="./icons/instagram.svg" alt="instagram icon"/>
        </a>
    </div>
  </div>
</template>

<script setup>
import ReadingSvg from './svgComponents/ReadingSvg.vue'
import { ref, onMounted } from 'vue';

const text = ref('')
const isTyping = ref(true)
const showIcons = ref(false)

onMounted(() => {
    text.value = "Welcome to my cozy little corner of the internet."
      setTimeout(() => {
        isTyping.value = false;
      }, 4600); // Change the timeout value according to your animation duration
})

</script>


<style scoped>
.home-page-wrapper {
    background-color: #E7CBCB;
    display: flex;
    justify-content: center;
    flex-direction: column;
}

.reading-svg{
    margin-top: 50px;
    align-self: center;
}

.welcome-text{
    align-self: center;
    margin-top: 30px;
    font-family: 'Roboto';
    font-style: normal;
    font-weight: 300;
    font-size: 24px;
    line-height: 28px;
    text-align: center;
    color: #643843;

    overflow: hidden; /* Ensures the content is not revealed until the animation */
    border-right: .15em solid #643843; /* The typwriter cursor */
    white-space: nowrap; /* Keeps the content on a single line */
    margin: 0 auto; /* Gives that scrolling effect as the typing happens */
    letter-spacing: .15em; /* Adjust as needed */
    animation: 
        typing 4.5s steps(40, end),
        blink-caret .5s step-end infinite; 
}

/* The typing effect */
@keyframes typing {
  from { width: 0 }
  to { width: 700px }
}

/* The typewriter cursor effect */
@keyframes blink-caret {
  from, to { border-color: transparent }
  50% { border-color: #643843; }
}

.explore-button{
    width: 165px;
    height: 38px;
    align-self: center;
    margin-top: 30px;
    border-radius: 16px;
    letter-spacing: 1px;
    text-shadow: 0 1px 0 rgba(0,0,0,0.01);
    border: 2px solid;
    border-color: #643843;
    color: #643843;
    font-family: 'Roboto';
    font-style: normal;
    font-weight: 300;
    font-size: 22px;
    display: flex;
    align-items: center;
    justify-content: center;
}

.explore-button:hover {
    background-color: #643843;
    color: #E7CBCB;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 5s;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}

.icons-container {
  display: flex;
  justify-content: center;
  margin-top: 20px;
}

.icon {
  margin: 0 15px;
  font-size: 20px;
}

</style>
