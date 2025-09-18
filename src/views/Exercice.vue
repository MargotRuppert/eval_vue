<template>
    <div class="card bg-base-100 w-96 shadow-sm">
        <div class="card-body">
            <img :src="img">
            <h2 class="card-title">{{ name }}</h2>
            <p>{{ age }}</p>
            <p>{{ numberRandom }}</p>
            <p>{{ ageAdd() }}</p>
            <input class="input input-accent" type="text" :value="name">
        </div>
    </div>
    <div>
        <Consignes v-on:click="clicked($event)" v-on:afficher="afficher($event)" :id="consignesExo.id" :globalObjective="consignesExo.globalObjective" :stepGoals="consignesExo.stepGoals"></Consignes>
    </div>

</template>

<script setup>
import { ref } from "vue";
import Consignes from "../components/Consignes.vue";

let img = ref("https://www.clipartmax.com/png/small/168-1681657_mario-classic-dr-mario-3d-model.png")
let name = "Dr Mario";
let age = 50;
let numberRandom = Math.random();

function ageAdd() {
    return age + 10;
}

//tableau objet pour consigne.vue
const consignesExo = ref({
    id: Math.random().toString(),
    globalObjective: 'Afficher dynamiquement les données du profil utilisateur DR Mario',
    stepGoals: [
        {
            description: 'Afficher le nom de l\'utilisateur avec template strings',
            isCompleted: false
        },
        {
            description: 'Afficher l\'âge de l\'utilisateur avec template strings',
            isCompleted: false
        }
        ,
        {
            description: 'Afficher l\'image de l\'utilisateur avec v-bind',
            isCompleted: false
        }
    ]
});

//toggle d'affichage du stepGoals
function afficher(step) {
    const toggleStep = consignesExo.value.stepGoals.find((element) => element.description === step);
    toggleStep.stepGoals = !toggleStep.stepGoals;

    console.log(toggleStep, "oui c'est bon")
}

//click des radio button
function clicked(step){
const click = consignesExo.value.stepGoals.find((element) => element.description === step);
    click.isCompleted = !click.isCompleted;
    console.log(click, "oui c'est bon")
}
</script>
