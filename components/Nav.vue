<template>
  <nav class="bg-white shadow-sm">
    <div class="container mx-auto">
      <div class="flex justify-around">
        <div class="flex">
          <a href="#" class="text-white text-3xl font-light p-3">
            <img src="../static/img/pet-hut-logo.png" />
          </a>
          <ul
            v-for="item in menu"
            :key="item.index"
            class="text-gray-400 sm:self-center text-md border-t sm:border-none"
          >
            <li class="sm:inline-block">
              <a :href="item.url" class="p-3 font-light text-gray-500 hover:text-gray-400">{{ item.text }}</a>
            </li>
          </ul>
        </div>
        <div class="flex justify-between gap-4 self-center">
          <a href="#" class="self-center text-gray-500 hover:text-gray-400 font-semibold">
            Entrar
          </a>
          <Button text="Cadastre-se" url="#" />
          <Button text="Quero adotar" url="#" secondary />
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: "Nav",
  props: {
    menu: {
      type: Array,
      default: () => [
        {
          index: 0,
          text: "Home",
          url: "#",
        },
      ],
    },
  },
}
</script>

<style scoped>

</style>
