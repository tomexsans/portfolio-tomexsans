<script setup>
const route = useRoute()
const isCurrentPage = (path) => {
    return route.fullPath == path ? 'active' : '';
}
const navigation = [
    ['Home','/','material-symbols:house-outline'],
    ['About Me','/about','material-symbols:smart-toy-outline-sharp'],
    ['My Projects','/projects','uil:github'],
    ['Contact Me','/contact','material-symbols:send-outline-rounded'],
];
</script>

<template>
    <div class="container mx-auto" >
        <div class="mt-10 mb-5">
            <div class="grid grid-cols-2 md:grid-cols-4">
                <div class="navigation" v-for="(name,key) in navigation" :key="key">
                    <NuxtLink :to="name[1]" :class="isCurrentPage(name[1])" >
                        <Icon :name="name[2]" class="mr-2" /> {{name[0]}}</NuxtLink>
                </div>
            </div>
        </div>
        <slot/>
    </div>

</template>

<style scoped>
.navigation{
    @apply text-xl text-center mb-5 md:mb-0;
}

.navigation a.active {
    @apply border-white text-white;
}
.navigation a.active svg {
    @apply animate-bounce hover:animate-ping;
}
.navigation a {
    @apply w-full block text-slate-400 font-bold border-b-4 border-transparent pb-2
    transition duration-1000 ease-in-out
        hover:border-slate-200 hover:text-slate-200;
}

.navigation a svg {
    @apply text-2xl mb-1 hover:animate-pulse;
}

.navigation a:hover svg {
    @apply animate-pulse duration-700 ease-in-out;
}
</style>