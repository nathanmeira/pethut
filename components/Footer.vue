<template>
  <footer class="bg-white" aria-labelledby="footer-heading">
    <hr>
    <h2 id="footer-heading" class="sr-only">Footer</h2>
    <div class="max-w-7xl mx-auto py-12 px-4 sm:px-6 lg:py-16 lg:px-8">
      <div class="xl:grid xl:grid-cols-3 xl:gap-8">
        <div class="space-y-8 xl:col-span-1">
          <img class="h-10" src="../static/img/pet-hut-logo.png" alt="Company name" />
          <p class="text-gray-500 text-base">Follow us on social media::</p>
          <ul id="social" class="space-x-8">
            <li>
              <a
                href="#"
                class="text-gray-500 hover:text-gray-700"
                target="_blank"
                rel="noopener noreferrer"
              >
                <Icon name="instagram-icon" />
              </a>
            </li>
            <li>
              <a
                href="#"
                class="text-gray-500 hover:text-gray-700"
                target="_blank"
                rel="noopener noreferrer"
              >
                <Icon name="twitter-icon" />
              </a>
            </li>
            <li>
              <a
                href="#"
                class="text-gray-500 hover:text-gray-700"
                target="_blank"
                rel="noopener noreferrer"
              >
                <Icon name="facebook-icon" />
              </a>
            </li>
          </ul>
          <div class="flex space-x-6">
            <a v-for="item in navigation" :key="item.name" :href="item.href" class="text-gray-400 hover:text-gray-500">
              <span class="sr-only">{{ item.name }}</span>
              <component :is="item.name" class="h-6 w-6" aria-hidden="true" />
            </a>
          </div>
        </div>
        <div class="mt-12 grid grid-cols-2 gap-8 xl:mt-0 xl:col-span-2">
          <div class="md:grid md:grid-cols-2 md:gap-8">
            <div>
              <h3 class="text-sm font-semibold text-gray-700 tracking-wider uppercase">Pet Hut</h3>
              <ul role="list" class="mt-4 space-y-4">
                <li v-for="item in navigation.about" :key="item.name">
                  <a :href="item.href" class="text-base text-gray-400 hover:text-gray-900 whitespace-nowrap">
                    {{ item.name }}
                  </a>
                </li>
              </ul>
            </div>
            <div class="mt-12 md:mt-0">
              <h3 class="text-sm font-semibold text-gray-700 tracking-wider uppercase">Terms</h3>
              <ul role="list" class="mt-4 space-y-4">
                <li v-for="item in navigation.terms" :key="item.name">
                  <a :href="item.href" class="text-base text-gray-400 hover:text-gray-900 whitespace-nowrap">
                    {{ item.name }}
                  </a>
                </li>
              </ul>
            </div>
          </div>
          <div class="md:grid md:grid-cols-2 md:gap-8 ml-20">
            <div>
              <h3 class="text-sm font-semibold text-gray-700 tracking-wider uppercase">Help</h3>
              <ul role="list" class="mt-4 space-y-4">
                <li v-for="item in navigation.help" :key="item.name">
                  <a :href="item.href" class="text-base text-gray-400 hover:text-gray-900 whitespace-nowrap">
                    {{ item.name }}
                  </a>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
      <div class="mt-12 border-t border-gray-200 pt-8">
        <p class="text-base text-gray-400 xl:text-center">Made with 💙 by <a class="underline" href="https://nnathan.com">Nathan</a> and <a class="underline" href="https://dribbble.com/br00nu">Bruno</a></p>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  props: {
    footer: {
      type: Object,
      required: true,
    },
  },
  computed: {
    navigation() {
      return this.footer.navigation;
    },
  }
}
</script>

<style scoped>
 #social li {
   display: inline-block;
 }
</style>
