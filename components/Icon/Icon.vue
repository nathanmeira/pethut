<template>
  <component
    :is="iconComponent"
    role="img"
  />
</template>

<script>
  const icons = {
    'facebook-icon': () => import(`./icons/social/FacebookIcon`),
    'twitter-icon': () => import(`./icons/social/TwitterIcon`),
    'instagram-icon': () => import(`./icons/social/InstagramIcon`),
    'location-icon': () => import(`./icons/LocationIcon`),
    'share-icon': () => import(`./icons/ShareIcon`),
    'save-icon': () => import(`./icons/SaveIcon`),
    'search-icon': () => import(`./icons/SearchIcon`),
    'playful-icon': () => import(`./icons/dog/PlayfulIcon`),
    'doggy-friendly-icon': () => import(`./icons/dog/DoggyFriendlyIcon`),
    'cat-friendly-icon': () => import(`./icons/dog/CatFriendlyIcon`),
    'child-friendly-icon': () => import(`./icons/dog/ChildFriendlyIcon`),
    'dog-age-icon': () => import(`./icons/dog/DogAgeIcon`),
    'dog-breed-icon': () => import(`./icons/dog/DogBreedIcon`),
    'dog-gender-icon': () => import(`./icons/dog/DogGenderIcon`),
    'dog-size-icon': () => import(`./icons/dog/DogSizeIcon`),
  }

  export default {
    name: 'Icon',

    props: {
      name: {
        type: String,
        required: true,
        validator(value) {
          return Object.prototype.hasOwnProperty.call(icons, value)
        },
      },
    },

    methods: {
      getIconsList() {
        return Object.keys(icons)
      },

      async iconComponent() {
        if (!icons[this.name]) {
          return
        }

        return await icons[this.name]()
      },
    },
  }
</script>
