<script setup>
import CyanButton from '../components/main/CyanButton.vue';
import ShortenLink from '../components/main/ShortenLink.vue'
import PreviousLink from '../components/main/PreviousLink.vue';
import StatisticCard from '../components/main/StatisticCard.vue'
import SectionText from '../components/main/SectionText.vue'

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
        <section id="CTA" class="mb-12">
            <div class="flex flex-col gap-y-8">
                <div class="overflow-hidden">
                    <figure class="w-[500px] ml-8">
                        <img class="w-full h-full" src="/images/illustration-working.svg" alt="illustration-working">
                    </figure>
                </div>
                <div class="flex flex-col text-center gap-y-4 px-5">
                    <SectionText
                        title = 'More than just shorter links'
                        paragraph = "Build your brand's recognition and get detailed insights on how your links are performing."
                        title-size = 'text-4xl'
                    />
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
            <div v-for="(link, index) in store.shortenedLinks" :key="index">
                <PreviousLink
                    :long-link = link.longLink
                    :short-link = link.shortLink
                />
            </div>
        </section>

        <section id="advanced-statistics">
            <div class="m-5 text-center">
                <SectionText
                    title = 'Advanced Statistics'
                    paragraph = 'Track how your links are performing across the web with our advanced statistics dashboard.'
                    title-size="text-2xl"

                    class="mt-20 mb-24"
                />

                <div class="flex flex-col items-center">
                    <StatisticCard
                    v-for="(feature, index) in features" :key="index"   
                    :obj = feature
                    :index = index
                    />
                </div>
            </div>

        </section>
    </main>


</template>

<style lang="scss" scoped>
@use '../style/scss/general' as *;

</style>