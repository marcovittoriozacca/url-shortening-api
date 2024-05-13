<script setup>

const socials = [
    {
        name: 'Facebook',
        thumb: 'images/icon-facebook.svg',
        url: 'https://www.facebook.com'
    },
    {
        name: 'Twitter',
        thumb: 'images/icon-twitter.svg',
        url: 'https://twitter.com'
    },
    {
        name: 'Pinterest',
        thumb: 'images/icon-pinterest.svg',
        url: 'https://it.pinterest.com/'
    },
    {
        name: 'Instagram',
        thumb: 'images/icon-instagram.svg',
        url: 'https://www.instagram.com/'
    },
]


</script>

<template>
    <div class="social-container">
        <a :href="social.url" v-for="(social, index) in socials" :key="index">
            <img :src="social.thumb" :alt="social.name">
        </a>
    </div>
</template>

<style lang="scss" scoped>
    
    .social-container{
        @apply flex gap-x-6 mt-7;
        img{
            @apply transition-transform duration-300 ease-out hover:scale-125;
        }
    }

</style>