<template>
    <div class="card-body shadow-xl">
        <h1 class="card-title text-primary">
            Nous contacter
        </h1>
        <fieldset class="fieldset bg-base-200 border-base-300 rounded-box w-xs border p-4">

            <label class="label">Name</label>
            <input type="text" class="input" v-model="name" />

            <label class="label">Email</label>
            <input v-model="email" @input="isEmailValid" />
            <p v-if="!isEmailValid && email" :style="{ backgroundColor: alerteColor}">Format d'email invalide.</p>
            <p v-else>l'email c'est good</p>

            <label class="label">Sujet</label>
            <input type="text" class="input" v-model="sujet" />

            <label class="label">Message</label>
            <input type="text" class="input" v-model="message" />
            <button class="btn bg-accent" @click="contact">Ajouter</button>
        </fieldset>
    </div>
</template>


<script setup>
import { ref } from 'vue';

const regex = /^[a-z0-9._-]+@[a-z0-9._-]+\.[a-z]{2,6}$/;
const alerteColor = ref('red');

function emailCheck() {
    isEmailValid = regex.test(this.email);
}

const name = ref("");
const email = ref("");
const sujet = ref("");
const message = ref("");


const emit = defineEmits({
    'contacter': (name, email) => {
        if (name, email) {
            return true;
        } else {
            console.log('name and email is required');
            console.warn('C\'est la catastrophe !!!!!!');
            console.error('ON A PAS DE EMAIL ET NAME Dans le event contacter');
            return false;
        }
    }
})





</script>