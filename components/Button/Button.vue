<template>
  <div>
    <button
      :to="url"
      type="button"
      :class="classList"
      class="inline-flex items-center border px-6 py-2 justify-center pointer rounded-full shadow-sm font-medium transition-all focus:outline-none"
      @click="onClick"
    >
      <div
        v-if="icon"
        class="mr-3"
        data-test="icon"
      >
        <Icon :name="`${icon}`" />
      </div>
      {{ text }}
    </button>
  </div>
</template>

<script>
export default {
  name: "Button",
  props: {
    text: {
      type: String,
      default: null,
    },
    url: {
      type: String,
      default: null,
    },
    secondary: Boolean,
    icon: {
      type: String,
      default: null
    },
    size: {
      type: String,
      default: null
    },
  },
  computed: {
    backgroundColor() {
      if (this.secondary) {
        return 'bg-white'
      }
      return 'bg-pet-primary hover:bg-orange-600'
    },
    color() {
      if (this.secondary) {
        return 'text-gray-600'
      }
      return 'text-white'
    },
    border() {
      if (this.secondary) {
        return 'border-gray-600'
      }
      return 'border-pet-primary hover:border-orange-600'
    },
    btnSize() {
      if (this.size === 'F') {
        return 'w-full'
      }

      return ''
    },
    classList() {
      return [
        this.backgroundColor,
        this.color,
        this.border,
        this.btnSize,
      ]
    },
  }
}
</script>

<style scoped>

</style>
