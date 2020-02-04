<template>
    <header class="bg-white border-b">
        <div class="flex items-center justify-between px-4 py-3">
            <div><img class="h-8" src="img/logo.svg" alt="logo"></div>
            <div>
                <button @click="isOpen = !isOpen" type="button" class="block text-black cursor-pointer focus:outline-none">
                    <svg v-if="isOpen" class="w-6 h-6 fill-current" stroke-width="2" xmlns="http://www.w3.org/2000/svg">
                        <path d="M18 6L6 18M6 6l12 12"/>
                    </svg>
                    <svg v-if="!isOpen" class="w-6 h-6 fill-current"  viewBox="0 0 32 32">
                        <path d="M4,10h24c1.104,0,2-0.896,2-2s-0.896-2-2-2H4C2.896,6,2,6.896,2,8S2.896,10,4,10z M28,14H4c-1.104,0-2,0.896-2,2  s0.896,2,2,2h24c1.104,0,2-0.896,2-2S29.104,14,28,14z M28,22H4c-1.104,0-2,0.896-2,2s0.896,2,2,2h24c1.104,0,2-0.896,2-2  S29.104,22,28,22z"/>
                    </svg>
                </button>
            </div>
        </div>
        <div :class="isOpen ? 'block border-t' : 'hidden'" class="px-2 pt-1 pb-2">
            <a class="block pl-2 text-teal-700 font-semibold py-2 hover:bg-teal-500" href="#">Link to Site</a>
            <a class="block pl-2 text-teal-700 font-semibold py-2 hover:bg-teal-500" href="#">Messages</a>
            <a class="block pl-2 text-teal-700 font-semibold py-2 hover:bg-teal-500" href="#">Tips</a>
        </div>
    </header>
</template>
<script>
    export default {
        data() {
            return {
                isOpen: false
            }
        },
        mounted() {
            console.log('Component mounted.')
        }
    }
</script>
