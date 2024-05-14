<script setup>
import { store } from "../../store.js";
import { ref } from "vue";
import axios from "axios";
import validUrl from "valid-url";

import CyanButton from "./CyanButton.vue";

//variables
let userLink = ref("");
let error = ref(false);

//functions
async function shortenUrl() {
  error.value = false;
  let encodedUrl = "";

  if (userLink.value === "") {
    error.value = true;
  }

  if (validateUrl(userLink.value)) {
    encodedUrl = encodeURIComponent(userLink.value);
  } else {
    error.value = true;
  }

  if (!error.value) {
    try {
      const response = await axios.post(
        `https://tinyurl.com/api-create.php?url=${encodedUrl}`,
      );
      const lastShortenedLink = response.data;
      error.value = false;

      const newShortLink = {
        longLink: userLink.value,
        shortLink: lastShortenedLink,
      };

      store.shortenedLinks.unshift(newShortLink);

      localStorage.setItem(
        "previousLink",
        JSON.stringify(store.shortenedLinks),
      );

      userLink.value = "";
    } catch (error) {
      console.error(error);
    }
  }
}
function validateUrl(url) {
  return validUrl.isUri(url);
}
</script>

<template>
  <div class="violet-banner m-5 rounded-md sm:m-0 lg:m-0 lg:mb-5">
    <div
      class="flex flex-col gap-y-9 p-6 lg:flex-row lg:items-center lg:gap-x-7 lg:p-14"
    >
      <div class="relative flex-1">
        <input
          v-model="userLink"
          class="w-full rounded border-2 px-5 py-3 focus:outline-none focus:ring-2"
          :class="[error ? 'input-error' : 'input-normal-state']"
          type="text"
          name="url"
          id="url"
          placeholder="Shorten a link here..."
        />
        <small
          v-if="error"
          :class="{
            'pointer-events-none absolute -bottom-5 left-0 select-none text-red-500 lg:-bottom-7 lg:text-lg':
              error,
          }"
          >Please add a link here</small
        >
      </div>
      <div class="lg:w-1/6">
        <CyanButton
          text="Shorten it!"
          :animation="true"
          class="rounded-md"
          @click="shortenUrl"
        />
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@use "../../style/scss/general" as *;

.violet-banner {
  background-image: url("/images/bg-shorten-mobile.svg");
  background-position: top right;
  background-repeat: no-repeat;
  background-size: contain;
  background-color: $dark-violet;
}

.input-error {
  @apply border-red-500 bg-rose-100 placeholder-red-600 focus:ring-red-600;
}
.input-normal-state {
  @apply border-white focus:ring-[#2acfcf];
}

@media screen and (min-width: 1024px) {
  .violet-banner {
    background-image: url("/images/bg-shorten-desktop.svg");
    background-size: cover;
  }
}
</style>
