<script setup>
import Navbar from '@/components/NavbarComponent.vue'
import Hero from '@/views/HeroView.vue'
import About from '@/views/AboutView.vue'
import Skills from '@/views/SkillsView.vue'
import Work from '@/views/WorkView.vue'
import Contact from '@/views/ContactView.vue'
import Footer from '@/components/FooterComponent.vue'
</script>

<template>
    <Navbar/>

    <section class="hero" id="Hero">
        <Hero/>
    </section>

    <section class="main_container" id="About">
        <About/>
    </section>

    <section class="main_container" id="Skills">
        <Skills/>
    </section>

    <section class="main_container" id="Work">
        <Work/>
    </section>
    
    <section class="main_container" id="Contact">
        <Contact/>
    </section>

    <Footer/>

</template>
