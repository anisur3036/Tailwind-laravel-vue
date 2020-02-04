<template>
  <header class="sm:flex sm:justify-between bg-white border-b sm:px-4 sm:py-0">
    <div class="flex items-center justify-between px-4 py-2 sm:ml-2">
      <div>
        <img class="w-8" src="img/logo.svg" alt="logo" />
      </div>
      <div>
        <button
          @click="isOpen = !isOpen"
          type="button"
          class="sm:hidden block text-black cursor-pointer focus:outline-none"
        >
          <svg class="w-5 h-5 fill-current" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
            <path v-if="!isOpen" fill-rule="evenodd" clip-rule="evenodd" d="M22 2V0H0v2h20zm0 4v2H0V6h20zm0 6v2H0v-2h20z"/>
            <path v-if="isOpen" fill-rule="evenodd" clip-rule="evenodd" d="M6 7.414l-4.293 4.293-1.414-1.414L4.586 6 .293 1.707 1.707.293 6 4.586 10.293.293l1.414 1.414L7.414 6l4.293 4.293-1.414 1.414L6 7.414z" />
          </svg>
        </button>
      </div>
    </div>
    <div :class="isOpen ? 'block border-t' : 'hidden'" class="sm:flex sm:items-center sm:justify-between px-2 pt-1 pb-2">
      <a class="block pl-2 text-teal-700 font-semibold py-2 hover:bg-teal-500 hover:text-white rounded sm:px-3" href="#">Link to Site</a>
      <a class="block pl-2 text-teal-700 font-semibold py-2 hover:bg-teal-500 hover:text-white rounded sm:mx-1 sm:px-3" href="#">Messages</a>
      <a class="block pl-2 text-teal-700 font-semibold py-2 hover:bg-teal-500 hover:text-white rounded sm:mx-1 sm:px-3" href="#">Tips</a>
      <a class="block pl-2 text-teal-700 font-semibold py-2 hover:bg-teal-500 hover:text-white rounded sm:mx-1 sm:px-3" href="#">Tips</a>
    </div>
  </header>
</template>
<script>
export default {
  data() {
    return {
      isOpen: false
    };
  },
  mounted() {
    console.log("Component mounted.");
  }
};
</script>
