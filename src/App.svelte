<script>
  import { onMount } from "svelte";

  const URL = "https://pokeapi.co/api/v2/pokemon";
  const imageUrl = `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/1.png`;
  let pokemon = [];
  onMount(async function () {
    const response = await fetch(URL);
    const json = await response.json();
    pokemon = json["results"];
    // console.log(pokemon);
  });
</script>

<main class="p-0">
  <div class="bg-green-100 py-6 min-h-screen">
    <h1 class="mt-6 mb-6 pb-6 text-center text-5xl text-green-600 font-bold">
      POKEMON
    </h1>

    <div class="flex items-center justify-center mt-6">
      <div
        class="grid grid-cols-1 gap-6 sm:grid-cols-2 md:grid-cols-2 lg:grid-cols-4 xl:grid-cols-4"
      >
        {#each pokemon as data, no}
          <!-- 1 card -->
          <div
            class="relative bg-white py-6 px-6 rounded-3xl w-64 my-4 shadow-xl"
          >
            <div
              class=" text-white flex items-center absolute rounded-full py-4 px-4 shadow-xl bg-yellow-500 left-4 -top-6"
            >
              <img
                src="https://cdn-icons-png.flaticon.com/512/361/361998.png"
                class="h-8 w-8"
                alt=""
              />
            </div>
            <div class="mt-8">
              <p class="text-xl font-semibold my-2">{data.name}</p>
              <img
                class="w-64"
                src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/{no +
                  1}.png"
                alt=""
              />
              <div class="flex space-x-2 text-gray-400 text-sm">
                <!-- svg  -->
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  class="h-5 w-5"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke="currentColor"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"
                  />
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"
                  />
                </svg>
                <p>Place</p>
              </div>
              <div class="flex space-x-2 text-gray-400 text-sm my-3">
                <!-- svg  -->
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  class="h-5 w-5"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke="currentColor"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z"
                  />
                </svg>
                <p>Date</p>
              </div>
            </div>
          </div>
        {/each}
      </div>
    </div>
  </div>
</main>

<!-- Section Hero -->
<style global>
  @tailwind base;
  @tailwind components;
  @tailwind utilities;
</style>
