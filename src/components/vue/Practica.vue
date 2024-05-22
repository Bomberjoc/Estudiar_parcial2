
<script setup>
    import { ref } from 'vue';

    let tasks = ref([])
    let inputTask = ref('')
    let change = ref(0)

    function addTask() {
        tasks.value.push(inputTask.value)
        inputTask.value = ''
        document.getElementById("inputTask").focus()
    }

    let bgs = ["bg-green-700 ","bg-red-700"]

    function color() {
        if(change.value == 0){
            change.value++
            document.getElementById("tareas").classList.add("hidden")
        }
        else{
            change.value--
            document.getElementById("tareas").classList.remove("hidden")

        }
    }

</script>

<template>
    <div class="flex flex-col items-center pt-[100px] bg-slate-50 shadow-lg mx-auto  mt-[150px] min-h-[600px] h-auto w-[750px] pb-6">
        <div class="flex items-center gap-10 mb-[30px]">
            <input id="inputTask" type="text" placeholder="Escribe aquí" v-model="inputTask" class="border border-blue-700 w-[330px] h-[30px] rounded-xl py-1 px-3 outline-none">
            <button class="border-2 border-black py-1 px-3 rounded-2xl hover:scale-110 duration-150" @click="addTask()">
                Agregar
            </button>
            <button class="border-2 border-black py-1 px-3 rounded-2xl hover:scale-110 duration-150 text-white" @click="color()" :class="bgs[change]" >
                Mostrar
            </button>
        </div>
        <div id="tareas">
            <div class="w-[330px] mb-[5px] " v-for="(task,index) in tasks" :key="index" >
                {{ task }}
            </div>  
        </div>
    </div>
</template>