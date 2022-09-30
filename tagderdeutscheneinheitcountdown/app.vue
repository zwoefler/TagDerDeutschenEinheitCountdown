<template>
  <div>
    <div
      class="
        min-w-screen min-h-screen
        bg-yellow-500
        flex
        items-center
        justify-center
        px-5
        py-5
      "
      x-data="beer()"
      x-init="start()"
    >
      <div class="text-yellow-100">
        <h1 class="text-6xl text-center mb-3 font-bold">
          Tag der deutschen Einheit!
        </h1>
        <div
          class="text-6xl text-center flex w-full items-center justify-center"
        >
          <div class="text-2xl mr-1 font-extralight">in</div>
          <div class="w-24 mx-1 p-2 bg-white text-yellow-500 rounded-lg">
            <div class="font-mono leading-none" x-text="days">{{ days }}</div>
            <div class="font-mono uppercase text-sm leading-none">Tagen</div>
          </div>
          <div class="w-24 mx-1 p-2 bg-white text-yellow-500 rounded-lg">
            <div class="font-mono leading-none" x-text="hours">{{ hours }}</div>
            <div class="font-mono uppercase text-sm leading-none">Stunden</div>
          </div>
          <div class="w-24 mx-1 p-2 bg-white text-yellow-500 rounded-lg">
            <div class="font-mono leading-none" x-text="minutes">{{ minutes }}</div>
            <div class="font-mono uppercase text-sm leading-none">Minuten</div>
          </div>
          <div class="text-2xl mx-1 font-extralight">und</div>
          <div class="w-24 mx-1 p-2 bg-white text-yellow-500 rounded-lg">
            <div class="font-mono leading-none" x-text="seconds">{{ seconds }}</div>
            <div class="font-mono uppercase text-sm leading-none">Sekunden</div>
          </div>
        </div>
      </div>
    </div>

    <!-- BUY ME A BEER AND HELP SUPPORT OPEN-SOURCE RESOURCES -->
    <div
      class="flex items-end justify-end fixed bottom-0 right-0 mb-4 mr-4 z-10"
    >
      <div>
        <a
          title="Buy me a beer"
          href="https://www.buymeacoffee.com/scottwindon"
          target="_blank"
          class="
            block
            w-16
            h-16
            rounded-full
            transition-all
            shadow
            hover:shadow-lg
            transform
            hover:scale-110 hover:rotate-12
          "
        >
          <img
            class="object-cover object-center w-full h-full rounded-full"
            src="https://i.pinimg.com/originals/60/fd/e8/60fde811b6be57094e0abc69d9c2622a.jpg"
          />
        </a>
      </div>
    </div>
  </div>
</template>


<script lang="ts" setup>
var deadline = new Date("Oct 3, 2022 00:00:00").getTime();
var days = ref(0)
var hours = ref(0)
var minutes = ref(0)
var seconds = ref(0)
var x = setInterval(function() {
  var now = new Date().getTime();
  var t = deadline - now;
  days.value = Math.floor(t / (1000 * 60 * 60 * 24));
  hours.value = Math.floor((t%(1000 * 60 * 60 * 24))/(1000 * 60 * 60));
  minutes.value = Math.floor((t % (1000 * 60 * 60)) / (1000 * 60));
  seconds.value = Math.floor((t % (1000 * 60)) / 1000);
  // Display the result in the element with id="demo"

  // If the count down is finished, write some text
  if (t < 0) {
    clearInterval(x);
  }
}, 1000);

// Import the functions you need from the SDKs you need

import { initializeApp } from "firebase/app";
import { getAnalytics } from "firebase/analytics";

// TODO: Add SDKs for Firebase products that you want to use
// https://firebase.google.com/docs/web/setup#available-libraries

// Your web app's Firebase configuration
// For Firebase JS SDK v7.20.0 and later, measurementId is optional
const firebaseConfig = {
  apiKey: "AIzaSyCwL4SFgkDg7Rm4njw3uwkLFeUQvsMgwog",
  authDomain: "tagderdeutscheneinheit-84a12.firebaseapp.com",
  projectId: "tagderdeutscheneinheit-84a12",
  storageBucket: "tagderdeutscheneinheit-84a12.appspot.com",
  messagingSenderId: "472373821537",
  appId: "1:472373821537:web:91805be43a997578f02a20",
  measurementId: "G-SJ3VWJDWMB"
};

// Initialize Firebase
const app = initializeApp(firebaseConfig);
const analytics = getAnalytics(app);

</script>
