<template>
  <nav class="bg-white shadow-sm">
    <div class="container mx-auto">
      <div class="flex justify-around">
        <div class="flex">
          <a href="#" class="text-white text-3xl font-light p-3">
            <img src="../static/img/pet-hut-logo.png" />
          </a>
          <ul
            v-for="page in pages"
            :key="page.id"
            class="text-gray-400 sm:self-center text-md border-t sm:border-none"
          >
            <li class="sm:inline-block">
              <a :href="page.link" class="p-3 font-light text-gray-500 hover:text-gray-400">{{ page.title }}</a>
            </li>
          </ul>
        </div>
        <div class="flex justify-between gap-4 self-center">
          <a href="#" class="self-center text-gray-500 hover:text-gray-400 font-semibold">
            Login
          </a>
          <Button text="Sign Up" url="#" />
          <Button text="Adopt a pet" url="#" secondary />
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: "Nav",
  props: {
    pages: {
      type: Array,
      default: () => null
    },
  },
}
</script>

<style scoped>

</style>
