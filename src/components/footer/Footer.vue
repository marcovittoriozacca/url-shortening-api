<script setup>
import SocialSection from "./SocialSection.vue";

const footerLinks = [
  {
    title: "Features",
    sublinks: [
      {
        name: "Link Shortening",
        url: "#",
      },
      {
        name: "Branded Links",
        url: "#",
      },
      {
        name: "Analytics",
        url: "#",
      },
    ],
  },
  {
    title: "Resources",
    sublinks: [
      {
        name: "Blog",
        url: "#",
      },
      {
        name: "Developers",
        url: "#",
      },
      {
        name: "Support",
        url: "#",
      },
    ],
  },
  {
    title: "Company",
    sublinks: [
      {
        name: "About",
        url: "#",
      },
      {
        name: "Our Team",
        url: "#",
      },
      {
        name: "Careers",
        url: "#",
      },
      {
        name: "Contact",
        url: "#",
      },
    ],
  },
];
</script>

<template>
  <footer>
    <section id="footer" class="py-12">
      <div
        class="flex flex-col items-center lg:container lg:mx-auto lg:flex-row lg:items-start lg:justify-between"
      >
        <figure class="mb-10">
          <img src="/images/white-logo.svg" alt="shortly" />
        </figure>
        <!-- loops for footer links -->
        <div class="flex flex-col gap-y-5 text-center lg:flex-row lg:gap-x-24">
          <ul v-for="(link, index) in footerLinks" :key="index">
            <li class="text-md mb-3 font-bold text-white">
              {{ link.title }}
            </li>
            <li
              v-for="(sublink, subIndex) in link.sublinks"
              :key="subIndex"
              class="mb-3"
            >
              <a
                :href="sublink.url"
                class="cyan-btn text-md font font-semibold text-gray-500"
              >
                {{ sublink.name }}
              </a>
            </li>
          </ul>
        </div>

        <SocialSection />
      </div>
    </section>
  </footer>
</template>

<style lang="scss" scoped>
@use "../../style/scss/general" as *;

section#footer {
  background-color: #232027;
}

.cyan-btn {
  @apply hover:text-[#2acfcf];
}
</style>
