<script setup>
import CyanButton from '../components/main/CyanButton.vue';
import ShortenLink from '../components/main/ShortenLink.vue'
import PreviousLink from '../components/main/PreviousLink.vue';
import StatisticCard from '../components/main/StatisticCard.vue'
import SectionText from '../components/main/SectionText.vue'
import BottomCTA from '../components/main/BottomCTA.vue'

import { store } from '../store';

//variables
const features = [
    {
        title: 'Brand Recognition',
        paragraph: "Boost your brand recognition with each click. Generic links don't mean a thing. Branded links help instill confidence in your content.",
        thumb: '/images/icon-brand-recognition.svg'
    },
    {
        title: 'Detailed Records',
        paragraph: "Gain insights into who is clicking your links. Knowing when and where people engage with your content helps inform better decisions.",
        thumb: '/images/icon-detailed-records.svg'
    },
    {
        title: 'Fully Customizable',
        paragraph: "Improve brand awareness and content discoverability through customizable links, supercharging audience engangement.",
        thumb: '/images/icon-fully-customizable.svg'
    }
]


</script>

<template>
    
    <main>
        <section id="CTA" class="mb-40 max-w-[640px] mx-auto lg:container">
            <div class="flex flex-col gap-y-8 lg:flex-row-reverse lg:items-center">

                <div class="overflow-hidden sm:flex sm:justify-center lg:w-1/2 lg:block">
                    <figure class="w-[500px] ml-8 sm:ml-0 lg:w-full">
                        <img class="w-full h-full" src="/images/illustration-working.svg" alt="illustration-working">
                    </figure>
                </div>

                <div class="flex flex-col text-center gap-y-4 px-5 lg:text-start lg:px-0 lg:w-1/2">
                    <SectionText
                        title = 'More than just shorter links'
                        paragraph = "Build your brand's recognition and get detailed insights on how your links are performing."
                        title-size = 'text-4xl lg:text-6xl'
                        class="lg:text-lg"
                    />
                    <div class="w-2/3 mx-auto mt-3 text-xl lg:mx-0 lg:w-1/4">
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

        <div class="bg-gray">
            <div class="t -translate-y-24 lg:-translate-y-20">
                <section id="shorten-link" class="max-w-[640px] mx-auto lg:container">
                    <ShortenLink/>
                    <div v-for="(link, index) in store.shortenedLinks" :key="index">
                        <PreviousLink
                            :long-link = link.longLink
                            :short-link = link.shortLink
                        />
                    </div>
                </section>
        
                <section id="advanced-statistics" class="max-w-[640px] mx-auto lg:container">
                    <div class="m-5 text-center">
                        <SectionText
                            title = 'Advanced Statistics'
                            paragraph = 'Track how your links are performing across the web with our advanced statistics dashboard.'
                            title-size="text-2xl lg:text-4xl"
        
                            class="my-24 lg:max-w-[492px] lg:mx-auto lg:text-lg"
                        />
        
                        <div class="flex flex-col items-center pb-20 lg:flex-row lg:pb-44">
                            <StatisticCard
                            v-for="(feature, index) in features" :key="index"   
                            :obj = feature
                            :index = index
                            />
                        </div>
                    </div>
                </section>
        
            </div>
            <section id="bottom-cta">
                <BottomCTA/>
            </section>
        </div>
        
    </main>


</template>

<style lang="scss" scoped>
@use '../style/scss/general' as *;

.bg-gray{
    background-color: #eff1f7;
}

</style>