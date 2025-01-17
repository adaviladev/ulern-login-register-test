<script setup>
import { ref } from "vue";
import AuthenticatedLayout from "@/Layouts/AuthenticatedLayout.vue";
import { Head } from "@inertiajs/vue3";

// Reactivity variables
const searchInput = ref("");
const pokemonName = ref("");
const pokemonId = ref("");
const weight = ref("");
const height = ref("");
const types = ref("");
const hp = ref("");
const attack = ref("");
const defense = ref("");
const spAttack = ref("");
const spDefense = ref("");
const speed = ref("");
const sprite = ref("");

// Functions for fetching Pokemon data
const getPokemon = async () => {
    try {
        const pokemonNameOrId = searchInput.value.toLowerCase();
        const response = await fetch(
            `https://pokeapi-proxy.freecodecamp.rocks/api/pokemon/${pokemonNameOrId}`
        );
        const data = await response.json();

        // Update the reactive variables
        pokemonName.value = data.name.toUpperCase();
        pokemonId.value = `#${data.id}`;
        weight.value = `Weight: ${data.weight}`;
        height.value = `Height: ${data.height}`;
        sprite.value = data.sprites.front_default;
        hp.value = data.stats[0].base_stat;
        attack.value = data.stats[1].base_stat;
        defense.value = data.stats[2].base_stat;
        spAttack.value = data.stats[3].base_stat;
        spDefense.value = data.stats[4].base_stat;
        speed.value = data.stats[5].base_stat;

        types.value =
            "Type: " +
            data.types
                .map(
                    (obj) =>
                        `<span class="type ${obj.type.name}">${obj.type.name}</span>`
                )
                .join("");
    } catch (err) {
        alert("Pokémon not found");
    }
};

const getRandomPokemon = async () => {
    const randomId =
        Math.random() < 0.5
            ? Math.floor(Math.random() * 1025) + 1
            : Math.floor(Math.random() * (10277 - 10001 + 1)) + 10001;
    try {
        const response = await fetch(
            `https://pokeapi-proxy.freecodecamp.rocks/api/pokemon/${randomId}`
        );
        const data = await response.json();
        // Update the reactive variables for random Pokémon
        pokemonName.value = data.name.toUpperCase();
        pokemonId.value = `#${data.id}`;
        weight.value = `Weight: ${data.weight}`;
        height.value = `Height: ${data.height}`;
        sprite.value = data.sprites.front_default;
        hp.value = data.stats[0].base_stat;
        attack.value = data.stats[1].base_stat;
        defense.value = data.stats[2].base_stat;
        spAttack.value = data.stats[3].base_stat;
        spDefense.value = data.stats[4].base_stat;
        speed.value = data.stats[5].base_stat;

        types.value =
            "Type: " +
            data.types
                .map(
                    (obj) =>
                        `<span class="type ${obj.type.name}">${obj.type.name}</span>`
                )
                .join("");
    } catch (err) {
        alert("Failed to fetch random Pokémon");
    }
};

// Reset display
const resetDisplay = () => {
    pokemonName.value = "";
    pokemonId.value = "";
    weight.value = "";
    height.value = "";
    types.value = "";
    hp.value = "";
    attack.value = "";
    defense.value = "";
    spAttack.value = "";
    spDefense.value = "";
    speed.value = "";
    sprite.value = "";
};

// Search Pokémon
const handleSearch = (e) => {
    e.preventDefault();
    getPokemon();
};

// Random Pokémon
const handleRandom = () => {
    getRandomPokemon();
};
</script>

<template>
    <Head title="Pokémon Search App" />

    <AuthenticatedLayout>
        <!-- <template #header>
            <h2 class="text-xl font-semibold leading-tight text-gray-800">
                Pokémon Search App
            </h2>
        </template> -->

        <div class="py-12">
            <div class="mx-auto max-w-7xl sm:px-6 lg:px-8">
                <div
                    class="overflow-hidden shadow-sm sm:rounded-lg bg-slate-900"
                >
                    <div class="p-6 text-slate-50 bg-slate-400">
                        <form
                            role="search"
                            @submit="handleSearch"
                            class="space-y-4"
                        >
                            <label for="search-input" class="block text-lg"
                                >Busca un Pokémon por su nombre o ID:</label
                            >
                            <input
                                type="text"
                                v-model="searchInput"
                                id="search-input"
                                required
                                class="p-2 border rounded-md w-full text-gray-950"
                            />
                            <button
                                class="btn btn-light bg-blue-500 text-white py-2 px-4 rounded-md"
                                type="submit"
                            >
                                Buscar
                            </button>
                        </form>
                        <button
                            class="btn btn-primary bg-green-500 text-white py-2 px-4 rounded-md mt-4"
                            @click="handleRandom"
                            type="button"
                        >
                            Show a random Pokémon
                        </button>

                        <div
                            class="identification mt-4 flex flex-col items-center"
                        >
                            <span
                                id="pokemon-name"
                                class="text-2xl font-bold"
                                >{{ pokemonName }}</span
                            >
                            <span
                                id="pokemon-id"
                                class="text-lg text-slate-50"
                                >{{ pokemonId }}</span
                            >
                        </div>

                        <div
                            class="type-and-size mt-4 flex justify-center gap-4"
                        >
                            <span
                                id="types"
                                class="block text-slate-50 text-lg"
                                v-html="types"
                            ></span>
                            <span id="weight" class="text-lg">{{
                                weight
                            }}</span>
                            <span id="height" class="text-lg">{{
                                height
                            }}</span>
                        </div>

                        <!-- <div class="types-and-sprite mt-4">
                            <div
                                class="sprite-container flex justify-center mt-4 text-lg h-48"
                            >
                                <img
                                    v-if="sprite"
                                    :src="sprite"
                                    alt="Pokémon sprite"
                                    class="w-30 h-30"
                                />
                            </div>
                        </div> -->

                        <div class="base-stats mt-4 bg-gray-100 p-1 rounded-md flex flex-wrap bg-slate-400 content-center items-center">
                            <div
                                class="sprite-container flex justify-center content-center flex-1 mt-4 text-lg h-48 items-center"
                            >
                                <img
                                    v-if="sprite"
                                    :src="sprite"
                                    alt="Pokémon sprite"
                                    class="w-30 h-30 align-middle"
                                />
                            </div>
                            <table
                                class="table-auto w-96 text-left border-separate border-spacing-2 border border-gray-100 bg-slate-900"
                            >
                                <tr>
                                    <td class="px-4 py-2">HP:</td>
                                    <td class="px-4 py-2 text-right">
                                        {{ hp }}
                                    </td>
                                </tr>
                                <tr>
                                    <td class="px-4 py-2">Attack:</td>
                                    <td class="px-4 py-2 text-right">
                                        {{ attack }}
                                    </td>
                                </tr>
                                <tr>
                                    <td class="px-4 py-2">Defense:</td>
                                    <td class="px-4 py-2 text-right">
                                        {{ defense }}
                                    </td>
                                </tr>
                                <tr>
                                    <td class="px-4 py-2">Sp. Attack:</td>
                                    <td class="px-4 py-2 text-right">
                                        {{ spAttack }}
                                    </td>
                                </tr>
                                <tr>
                                    <td class="px-4 py-2">Sp. Defense:</td>
                                    <td class="px-4 py-2 text-right">
                                        {{ spDefense }}
                                    </td>
                                </tr>
                                <tr>
                                    <td class="px-4 py-2">Speed:</td>
                                    <td class="px-4 py-2 text-right">
                                        {{ speed }}
                                    </td>
                                </tr>
                            </table>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>

<style scoped>
/* Custom Tailwind overrides for specific types */
.type {
    width: 66px;
    padding: 5px;
    font-size: 0.7rem;
    text-align: center;
    border-radius: 5px;
    text-transform: uppercase;
}

.normal {
    background-color: #b7b7aa;
}

.fire {
    background-color: #ff6f52;
}

.water {
    background-color: #42a1ff;
}

.electric {
    background-color: #fecc33;
}

.grass {
    background-color: #78cc55;
}

.ice {
    background-color: #66ccfe;
}

.fighting {
    background-color: #d3887e;
}

.poison {
    background-color: #c68bb7;
}

.ground {
    background-color: #dfba52;
}

.flying {
    background-color: #8899ff;
}

.psychic {
    background-color: #ff66a3;
}

.bug {
    background-color: #aabb23;
}

.rock {
    background-color: #baaa66;
}

.ghost {
    background-color: #9995d0;
}

.dragon {
    background-color: #9e93f1;
}

.dark {
    background-color: #b59682;
}

.steel {
    background-color: #abaabb;
}

.fairy {
    background-color: #ed99ed;
}
</style>
