<template>
    <section class="py-10 lg:py-20 bg-green-600"><div class="container mx-auto px-4">
        <iframe name="dummyframe" id="dummyframe" style="display: none;"></iframe>
  <div class="max-w-xl mx-auto">
    <div class="mb-10">
      <a class="text-white text-3xl font-bold leading-none" href="#">
        <img class="mx-auto" src="atis-assets/logo/atis/atis-mono-light.svg" alt="" width="auto" data-removed="true"></a>
    </div>
    <div class="mb-6 lg:mb-10 p-6 lg:p-12 bg-white shadow-md rounded">
      <div class="mb-6">
        <h3 class="text-2xl font-bold">Contactez moi</h3>
      </div>
      <form method="POST" action="https://script.google.com/macros/s/AKfycbw5tul6kA235BNmHgkEk5piZGcf3dzkP-6UNyawG-MBN9GJmY1o2aPEycvBIHAzKGyd/exec" target="dummyframe">
        <div class="flex flex-wrap -mx-2">
          <div class="mb-3 w-full lg:w-1/2 px-2">
            <input class="w-full p-4 text-xs bg-gray-50 outline-none rounded" type="text" placeholder="Nom" id="firstname" name="firstname"></div>
          <div class="mb-3 w-full lg:w-1/2 px-2">
            <input class="w-full p-4 text-xs bg-gray-50 outline-none rounded" type="text" placeholder="Prénom" id="lastname" name="lastname"></div>
        </div>
        <div class="mb-3 flex p-4 bg-gray-50 rounded">
          <input class="w-full text-xs bg-gray-50 outline-none" type="email" placeholder="name@email.com" name="email"><svg class="h-6 w-6 ml-4 my-auto text-gray-300" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 12a4 4 0 10-8 0 4 4 0 008 0zm0 0v1.5a2.5 2.5 0 005 0V12a9 9 0 10-9 9m4.5-1.206a8.959 8.959 0 01-4.5 1.207"></path></svg></div>
        <div class="mb-6 flex p-4 bg-gray-50 rounded" data-removed="true">
            <textarea class="appearance-none w-full p-4 text-xs font-semibold leading-none bg-gray-50 rounded outline-none" name="message" rows="3" placeholder="Ecrivez moi quelque chose..."></textarea>
        </div>
        <div class="text-center">
          <button class="mb-2 w-full py-4 bg-green-600 hover:bg-green-700 rounded text-sm font-bold text-gray-50 transition duration-200" v-on:click="popup = true">Envoyer</button>
          <div v-if="popup" role="alert" class="bg-teal-100 border-t-4 border-teal-500 rounded-b text-teal-900 px-4 py-3 shadow-md bg-green-300"><div class="flex"><div class="py-1"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" class="fill-current h-6 w-6 text-teal-500 mr-4"><path d="M2.93 17.07A10 10 0 1 1 17.07 2.93 10 10 0 0 1 2.93 17.07zm12.73-1.41A8 8 0 1 0 4.34 4.34a8 8 0 0 0 11.32 11.32zM9 11V9h2v6H9v-4zm0-6h2v2H9V5z"></path></svg></div> <div><p class="font-bold">Merci, votre message à bien été envoyer</p> <p class="text-sm">Je vous répondrais dans les plus brefs délais</p></div></div></div>
        </div>
      </form>
    </div>
  </div>
  </div>
</section>
</template>
<script>
export default {
    data(){
        return  {
            popup: false
        }
    }
}
</script>