<template>
  <div>
    <Nav :pages="pages" />
    <div class="max-w-5xl mx-auto grid grid-cols-1 mt-10">
      <div class="grid overflow-hidden grid-cols-4 grid-rows-2 gap-5">
        <div class="box row-start-1 row-span-2 col-start-1 col-end-3">
          <img
            src="../static/img/dogs/dog1.png"
            alt=""
            class="w-[500px] h-full object-cover rounded-lg"
            loading="lazy"
          />
        </div>
        <div class="box row-start-1 col-start-3 col-end-4">
          <img
            src="../static/img/dogs/dog2.png"
            alt=""
            class="w-full h-full object-cover rounded-lg"
            loading="lazy"
          />
        </div>
        <div class="box col-start-4 col-end-4">
          <img
            src="../static/img/dogs/dog3.png"
            alt=""
            class="w-full h-full object-cover rounded-lg"
            loading="lazy"
          />
        </div>
        <div class="box col-start-3 col-end-4">
          <img
            src="../static/img/dogs/dog4.png"
            alt=""
            class="w-full h-full object-cover rounded-lg"
            loading="lazy"
          />
        </div>
        <div class="box col-start-4 col-end-4">
          <img
            src="../static/img/dogs/dog5.png"
            alt=""
            class="w-full h-full object-cover rounded-lg"
            loading="lazy"
          />
        </div>
      </div>
      <div
        class="grid overflow-hidden grid-cols-5 grid-rows-2 gap-2 mt-8 justify-between"
      >
        <div class="box row-start-1 row-end-4 col-start-1 col-end-4">
          <div>
            <span class="text-xl font-bold text-pet-primary">{{ dogProfiles.name }}</span>
            <div v-if="dogProfiles" class="flex mt-4 text-gray-600">
              <Icon name="location-icon" />
              <span class="self-center ml-3">{{ dogProfiles.location }}</span>
              <span class="ml-3"> | </span>
              <span class="self-center ml-3">Rescued in {{ dateFormatter(dogProfiles.rescueDate) }}</span>
            </div>
            <div class="mt-4">
              <div
                class="grid overflow-hidden grid-cols-4 grid-rows-1 gap-0 border border-pet-primary rounded-tl-lg rounded-tr-lg rounded-br-lg rounded-bl-lg"
              >
                <span
                  v-for="item in dogProfile.info
"
                  :key="item.index"
                  class="px-4 py-7 bg-[#fff8f7] text-pet-primary text-sm flex justify-center row-start-1"
                >
                  <Icon class="self-center" :name="item.type+'-icon'" />
                  <span class="self-center ml-3 whitespace-nowrap">{{item.value}}</span>
                </span>
              </div>
            </div>
            <div class="mt-6">
              <div id="description">
                <p class="text-lg font-bold text-gray-600">{{ dogProfiles.name }}'s history:</p>
                <div class="mb-3 mt-3 text-gray-500">
                  <p>
                    {{ dogProfiles.description }}
                  </p>
                </div>
              </div>
            </div>
            <hr>
            <div class="mt-6">
              <p class="text-lg font-bold text-gray-600">{{ dogProfiles.name }}'s characteristics:</p>
            </div>
            <div class="flex justify-between">
              <div
                v-for="item in dogProfile.characteristics"
                :key="item.index"
                class="w-1/4 mt-6 p-4 mx-2 border shadow-lg rounded-md text-sm"
              >
                <Icon :name="item.type+'-icon'" />
                <p class="mt-4">{{item.value}}</p>
              </div>
            </div>
            <hr class="mt-6">
          </div>
        </div>
        <div class="box row-start-1 row-end-4 col-start-4 col-end-6">
          <div class="flex w-full ml-24">
            <button
              href="#"
              class="inline-flex items-center gap-2 bg-[#fff8f7] text-pet-primary hover:bg-orange-100 px-6 py-2 mr-3 pointer rounded-full shadow-sm font-medium transition-all focus:outline-none"
            >
              <Icon name="share-icon" />
              Share
            </button>
            <button
              href="#"
              class="inline-flex items-center gap-2 bg-[#fff8f7] text-pet-primary hover:bg-orange-100 px-6 py-2 pointer rounded-full shadow-sm font-medium transition-all focus:outline-none"
            >
              <Icon name="save-icon" />
              Save
            </button>
          </div>
          <div class="flex mt-6 ml-4 p-4 border shadow-lg rounded-md">
            <div class="p-3">
              <p class="text-lg font-bold text-gray-600">I want to adopt {{ dogProfile.name }}</p>
              <p class="mb-5 mt-3 text-gray-500">
                To adopt this puppy, we need to get to know you better.
                Click the button below to complete our adoption form and,
                if selected, we will get back to you within 3 business days
                after completing this form.
              </p>
              <Button
                size="F"
                text="I want to adopt"
                url="#" />
            </div>
          </div>
          <div class="flex mt-4 ml-4 p-4 border rounded-md items-center">
            <Icon name="search-icon" class="self-center mr-2" />
            <p class="ml-4 mb-3 mt-3 text-gray-600">
              <span class="text-pet-primary">{{ dogProfile.peopleInterested}} people </span> have already shown interest to adopt this puppy
            </p>
          </div>
        </div>
      </div>
      <div class="mt-6">
        <p class="text-lg font-bold text-gray-600">Other puppies waiting for a home</p>
      </div>
      <div class="flex gap-2">
        <div v-for="dog in dogsList" :key="dog.index" class="mt-6 w-1/4 rounded-md overflow-hidden shadow-lg">
          <div class="m-4">
            <img class="mt-3 w-full rounded-md" src="../static/img/dogs/dog4.png" alt="Dog picture" loading="lazy">
          </div>
          <div class="px-6 py-4">
            <div class="text-lg font-bold text-gray-600 mb-2">{{ dog.name }}</div>
            <div class="flex mt-4 max-h-6 text-gray-500">
              <Icon name="location-icon" />
              <span class="self-center ml-3 line-clamp">{{ dog.location }}</span>
            </div>
          </div>
        </div>
      </div>
      <div class="w-full mt-10 mb-10 flex justify-center">
        <Button text="Veja todos" url="#" />
      </div>
    </div>
    <Footer :footer="footer" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      dog: [],
      menu: [],
      footerItems: [],
      dogProfile: {
        peopleInterested: 8,
        info: [
          {
            type: 'dog-age',
            value: '1 ano',
          },
          {
            type: 'dog-breed',
            value: 'Vira-lata',
          },
          {
            type: 'dog-gender',
            value: 'Macho',
          },
          {
            type: 'dog-size',
            value: 'Pequeno',
          },
        ],
        characteristics: [
          {
            type: 'playful',
            value: 'Brincalhão',
          },
          {
            type: 'cat-friendly',
            value: 'Convive bem com gatos',
          },
          {
            type: 'child-friendly',
            value: 'Convive bem com crianças'
          },
          {
            type: 'doggy-friendly',
            value: 'Convive bem com outros cachorros'
          },
        ],
      },
      dogsList: [
        {
          name: 'Apollo',
          location: 'São José dos Campos - SP',
          picture: 'dog1.png',
        },
        {
          name: 'Lili',
          location: 'Limeira - SP',
          picture: 'dog2.png',
        },
        {
          name: 'Alfredo',
          location: 'Barueri - SP',
          picture: 'dog3.png',
        },
        {
          name: 'Mel',
          location: 'Limeira - SP',
          picture: 'dog4.png',
        },
      ]
    }
  },
  async fetch() {
    this.dog = await fetch(
      'http://localhost:1337/api/dogs/1?populate=*'
    ).then(res => res.json())

    this.menu = await fetch(
      'http://localhost:1337/api/menu?populate=*'
    ).then(res => res.json())

    this.footerItems = await fetch(
      'http://localhost:1337/api/footer?populate[navigation][populate]=*'
    ).then(res => res.json())
  },
  computed: {
    dogProfiles() {
      return this.dog.data.attributes || []
    },
    dogPictures() {
      return this.dog.data.attributes.pictures || []
    },
    dogInfo() {
      return this.dog.data.attributes.information || []
    },
    dogCharacteristics() {
      return this.dog.data.attributes.characteristics || []
    },
    pages() {
      return this.menu.data.attributes.menuPage || []
    },
    footer() {
      return this.footerItems.data.attributes || []
    }
  },
  methods: {
    dateFormatter(date) {
      const dateFormatted = new Date(date)
      return dateFormatted.toLocaleDateString('en-CA', {
        day: 'numeric',
        month: 'long',
        year: 'numeric',
      })
    },
  }
}


</script>

<style scoped>
  #description p {
    @apply mb-8;
  }

  .line-clamp {
    display: -webkit-box;
    -webkit-line-clamp: 1;
    -webkit-box-orient: vertical;
    overflow: hidden;
  }
</style>
