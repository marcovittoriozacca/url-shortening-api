<script setup>
import CyanButton from '../components/main/CyanButton.vue';
import ShortenLink from '../components/main/ShortenLink.vue'
</script>

<template>
    
    <main>
        <section id="CTA" class="mb-12">
            <div class="flex flex-col gap-y-8">
                <div class="overflow-hidden">
                    <figure class="w-[500px] ml-8">
                        <img class="w-full h-full" src="/images/illustration-working.svg" alt="illustration-working">
                    </figure>
                </div>
                <div class="flex flex-col text-center gap-y-4 px-5">
                    <h2 class="font-extrabold text-4xl text-very-dark-blue">More than just shorter links</h2>
                    <p>Build your brand's recognition and get detailed insights on how your links are performing.</p>
                    <div class="w-2/3 mx-auto mt-3 text-xl">
                        <a href="#">
                            <CyanButton
                                text = 'Get Started'
                                :animation = true
                            />
                        </a>
                    </div>
                </div>
            </div>
        </section>

        <section id="shorten-link">
            
            <ShortenLink/>
            
        </section>
    </main>


</template>

<style lang="scss" scoped>
@use '../style/scss/general' as *;

.text-very-dark-blue{
    color: $very-dark-blue;
}
</style>