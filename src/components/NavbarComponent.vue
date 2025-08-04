<script setup>
import { ref } from 'vue';

const isNavOpen = ref(false);

const toggleNav = () => {
    isNavOpen.value = !isNavOpen.value;
};
const closeNav = () => {
    isNavOpen.value = false;
};

</script>

<template>
    <div class="nav_container">
        <div class="logo">
            <img src="../assets/images/dell.jpg" width="40px" height="40px" alt="logo">
            <a href="#Hero" @click="closeNav">Developer</a>
        </div>
        <div class="nav_links" :class="{ 'active': isNavOpen }">
            <ul>
                <li><a href="#About"  @click="closeNav" >About</a></li>
                <li><a href="#Skills"  @click="closeNav" >Skills</a></li>
                <li><a href="#Work"  @click="closeNav" >Work</a></li>
                <li><a href="#Contact"  @click="closeNav" >Contact</a></li>
            </ul>
        </div>
        <div class="burger" @click="toggleNav" :class="{ 'active': isNavOpen }">
            <span></span>
            <span></span>
            <span></span>
        </div>
    </div>
</template>