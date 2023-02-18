<template>
  <div class="flex items-center justify-center h-screen">
    <div class="w-full max-w-md">
    <p class="font-bold text-4xl mb-4 text-center">Name Statistics</p>
    <p class="font-medium text-xl mb-4 text-center">Find out the number of masculine and feminine names in your list.</p>
    <p class="text-md mb-4 text-center">Paste a list of names below, separating each name by comma:</p>
      <textarea
        v-model="namesList"
        placeholder="Nathan, John, Mary, Jane..."
        class="border border-gray-400 rounded-lg p-2 w-full"
      ></textarea>
      <span v-if="namesList.length" @click="namesList = []" class="text-sm text-blue-600 cursor-pointer">Clear list</span>
      <button
        class="bg-blue-500 text-white py-2 px-4 rounded-lg mt-2 w-full hover:bg-blue-600"
        @click="countNames"
      >
        Count Names
      </button>
      <div v-if="loading" class="flex justify-center">
        <Loading />
      </div>
      <div v-else class="flex mt-4 gap-4 text-center">
        <div class="w-1/2 p-4 bg-gray-100 rounded-lg shadow-md">
          <p class="font-bold text-lg">Feminine Names:</p>
          <p class="text-2xl">{{ feminineCount }}</p>
        </div>
        <div class="w-1/2 p-4 bg-gray-100 rounded-lg shadow-md text-center">
          <p class="font-bold text-lg">Masculine Names:</p>
          <p class="text-2xl">{{ masculineCount }}</p>
        </div>
      </div>
      <div v-if="notFound.length > 0">
        <p class="mt-4 font-bold text-center text-lg">Names Not Found: {{ notFound.length }}</p>
        <ul v-if="notFound.length > 0" class="mt-4 rounded-lg shadow-md bg-gray-100 p-4 h-64 overflow-auto">
          <li v-for="name in notFound" :key="name.index" class="py-2 font-medium capitalize">{{ name }}</li>
        </ul>
      </div>
    </div>
  </div>
</template>
<script>
import Loading from "~/components/Icons/Loading.vue";

export default {
  components: {Loading},
  data() {
    return {
      namesList: "",
      masculineCount: 0,
      feminineCount: 0,
      loading: false,
      notFound: []
    };
  },
  methods: {
    async countNames() {
      this.loading = true;
      this.notFound = [];
      this.feminineCount = 0;
      this.masculineCount = 0;

      const names = this.namesList.split(",").map(name => name.trim().toLowerCase());

      const masculineNames = [
        "Aaron",
        "Adam",
        "Adrian",
        "Aiden",
        "Alexander",
        "Andrew",
        "Angel",
        "Anthony",
        "Asher",
        "Austin",
        "Axel",
        "Benjamin",
        "Brooks",
        "Caleb",
        "Cameron",
        "Carson",
        "Carter",
        "Charles",
        "Christian",
        "Christopher",
        "Colton",
        "Connor",
        "Cooper",
        "Daniel",
        "David",
        "Dominic",
        "Dylan",
        "Easton",
        "Eli",
        "Elias",
        "Elijah",
        "Ethan",
        "Everett",
        "Ezekiel",
        "Ezra",
        "Gabriel",
        "Grayson",
        "Greyson",
        "Henry",
        "Hudson",
        "Hunter",
        "Ian",
        "Isaac",
        "Isaiah",
        "Jace",
        "Jack",
        "Jackson",
        "Jacob",
        "James",
        "Jameson",
        "Jaxon",
        "Jaxson",
        "Jayden",
        "Jeremiah",
        "John",
        "Jonathan",
        "Jordan",
        "Jose",
        "Joseph",
        "Joshua",
        "Josiah",
        "Julian",
        "Kai",
        "Kayden",
        "Landon",
        "Leo",
        "Leonardo",
        "Levi",
        "Liam",
        "Lincoln",
        "Logan",
        "Luca",
        "Lucas",
        "Luke",
        "Mason",
        "Mateo",
        "Matthew",
        "Maverick",
        "Michael",
        "Miles",
        "Nathan",
        "Nicholas",
        "Noah",
        "Nolan",
        "Oliver",
        "Owen",
        "Parker",
        "Robert",
        "Roman",
        "Ryan",
        "Samuel",
        "Santiago",
        "Sebastian",
        "Silas",
        "Theodore",
        "Thomas",
        "Wesley",
        "William",
        "Wyatt",
        "Xavier"
      ].map(name => name.toLowerCase());
      const feminineNames = [
        "Abigail",
        "Ada",
        "Adalyn",
        "Adalynn",
        "Addison",
        "Adeline",
        "Aliana",
        "Alina",
        "Amelia",
        "Amelia",
        "Anastasia",
        "Anna",
        "Aria",
        "Ariana",
        "Aubrey",
        "Audrey",
        "Ava",
        "Avery",
        "Avery",
        "Brinley",
        "Brooklyn",
        "Callie",
        "Carly",
        "Charlotte",
        "Chloe",
        "Dahlia",
        "Delaney",
        "Eliana",
        "Elizabeth",
        "Ella",
        "Ellie",
        "Eloise",
        "Melissa",
        "Amy",
        "Luiza",
        "Jane",
        "Elsie",
        "Emery",
        "Emily",
        "Emma",
        "Estrella",
        "Evelyn",
        "Everly",
        "Felicity",
        "Finley",
        "Galiana",
        "Genesis",
        "Genevieve",
        "Grace",
        "Harper",
        "Harper",
        "Harper",
        "Harper",
        "Hazel",
        "Iris",
        "Isabella",
        "Josephina",
        "Josephine",
        "Journee",
        "Kali",
        "Kaylee",
        "Kehlani",
        "Kennedy",
        "Lara",
        "Layla",
        "Leilani",
        "Lillian",
        "Lily",
        "Luna",
        "Madison",
        "Magnolia",
        "Mariah",
        "Marlowe",
        "Mia",
        "Mila",
        "Molly",
        "Mya",
        "Natalie",
        "Nevaeh",
        "Nora",
        "Olivia",
        "Paisley",
        "Penelope",
        "Phoenix",
        "Presley",
        "Pumpkin",
        "Raelynn",
        "Remi",
        "Riley",
        "Rowan",
        "Rylee",
        "Sadie",
        "Savannah",
        "Saylor",
        "Scarlett",
        "Serenity",
        "Skylar",
        "Sofia",
        "Sophia",
        "Victoria",
        "Waverly",
        "Willow",
        "Ximena",
        "Zoe"
      ].map(name => name.toLowerCase());

      await new Promise(resolve => {
        for (const name of names) {
          if (feminineNames.includes(name)) {
            this.feminineCount++;
          } else if (masculineNames.includes(name)) {
            this.masculineCount++;
          } else {
            this.notFound.push(name);
          }
        }

        resolve();
      });

      this.loading = false;
    }
  }
};
</script>
