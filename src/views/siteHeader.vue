<script setup>
    import dropDown from '../components/dropDown.vue';
    import baseInput from '../components/baseInput.vue';
    import { ref, defineComponent, onMounted, computed } from 'vue';
    import {gsap} from 'gsap';
    const emit = defineEmits(['openLogin'])

    const Logo = ref('')

    const openLoginTemplate = () =>{
        emit('openLogin')
    }
    const typeOfScreen = ref({
        sm:false,
        md:false
        })
    const isSmallScreen = computed(()=>{
        if(window.innerWidth <= 900){
            typeOfScreen.sm = !typeOfScreen.sm
            return typeOfScreen;
        }
    })
    
    /*computed(() => window.innerWidth <=900)*/

    const getData = (inputValue) =>{
        let userQuery = inputValue
        console.log('You have writen ' + userQuery)
        }
    
    const firstAnimation = ()=> {
        const tl = gsap.timeline({delay:1,paused:true});
            tl.to((Logo.value, {x:'-800',autoAlpha:0, duration:1}))    
        
    }
    
/* <searchIcon 
        class="h-full w-12 border-r-2 border-great-blue-300 hover:text-great-blue-300">

    </searchIcon>
*/
</script>

<template>
    <header class="w-full">
       <div class="flex w-full h-full justify-center items-center">
            
            <div class="flex-grow bg-white h-1/2 py-1 rounded mx-4 shadow-md items-center">
                <div class="flex h-full sitems-center justify-center ">
                    
                    <baseInput 
                        :sendInput="true" 
                        @send-query="getData"
                        class=" flex-grow "
                        placeholder=" Hi!"/>
                    
                    <dropDown 
                        class=" w-20 border-l-2 border-great-blue-300 xs:hidden"/>
                </div>
                
            </div>
            <button 
                id="Login" 
                class="h-3/5 w-16 bg-great-blue-300 hover:bg-great-blue-400 font-Roboto font rounded-lg shadow-md text-center align-middle sm:hidden"
                @click="openLoginTemplate">
                Login
            </button>
        </div> 
    </header>
</template>



<style>
    @import url('https://fonts.googleapis.com/css2?family=Roboto:ital,wght@1,100&display=swap');
</style>