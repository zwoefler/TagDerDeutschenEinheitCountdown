<template>
  <div>
    <Head>
      <Title>{{ hours_until }} Std. bis zum {{ title }}</Title>
      <Meta name="description" content="Verpass nicht den Jahrestags unseres geliebten Vaterlandes!" />
      <Meta property="og:title" :content="`${ title }`" />
      <Meta property="og:description" content="Verpass nicht den Jahrestags unseres geliebten Vaterlandes!"/>
      <Meta property="og:type" content="website" />
      <Meta property="og:site_name" content="Tag der deutschen Einheit" />
      <Meta property="og:url" content="https://countdown.tag-der-deutschen-einheit.org" />
    </Head>
    <div
      class="
        min-w-screen min-h-screen
        bg-gray-900
        flex
        items-center
        justify-center
      "
    >
      <div class="text-gray-100">
        <h1 class="text-5xl md:text-8xl text-center mb-3 font-bold">
          <p>Tag der</p>
          <p class="text-yellow-500">deutschen</p>
          <p>Einheit!</p>
        </h1>
        <div
          class="text-6xl text-center flex flex-col space-y-2 md:flex-row w-full items-center justify-center"
        >
          <div class="text-2xl mr-1 font-extralight">in</div>
          <div class="w-32 mx-1 p-2 bg-black rounded-lg">
            <div class="font-mono leading-none" x-text="days">{{ days }}</div>
            <div class="font-mono uppercase text-sm leading-none">Tagen</div>
          </div>
          <div class="w-32 mx-1 p-2 bg-red-500 rounded-lg">
            <div class="font-mono leading-none" x-text="hours">{{ hours }}</div>
            <div class="font-mono uppercase text-sm leading-none">Stunden</div>
          </div>
          <div class="w-32 mx-1 p-2 bg-yellow-500 rounded-lg">
            <div class="font-mono leading-none" x-text="minutes">{{ minutes }}</div>
            <div class="font-mono uppercase text-sm leading-none">Minuten</div>
          </div>
          <div class="text-2xl mx-1 font-extralight">und</div>
          <div class="w-32 mx-1 p-2 bg-gray-400 rounded-lg">
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
          title="Kauf mirn Bier"
          href="https://www.buymeacoffee.com/martinzwoelfer"
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
const title = "Tag der dt. Einheit"
var deadline = new Date("Oct 3, 2023 00:00:00").getTime();
var days = ref(0)
var hours_until = ref(0)
var hours = ref(0)
var minutes = ref(0)
var seconds = ref(0)
var x = setInterval(function() {
  var now = new Date().getTime();
  var t = deadline - now;
  days.value = Math.floor(t / (1000 * 60 * 60 * 24));
  hours_until.value = Math.floor(t / (1000 * 60 * 60));
  hours.value = Math.floor((t%(1000 * 60 * 60 * 24))/(1000 * 60 * 60));
  minutes.value = Math.floor((t % (1000 * 60 * 60)) / (1000 * 60));
  seconds.value = Math.floor((t % (1000 * 60)) / 1000);

}, 1000);

</script>
