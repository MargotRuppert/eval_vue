<template>
    <div class="card card-dash bg-base w-full">
        <div class="card-body">
            <h2 class="card-title">Consignes</h2>
            <p>{{ id }}</p>
            <p>{{ globalObjective }}</p>
            <ul class="list bg-base rounded-box" >
                <li class="list-row" v-for="goal in props.stepGoals" v-if="stepGoals">
                    <div>{{ goal.description }}</div>
                    <input type="checkbox" checked="checked" class="checkbox checkbox-primary" v-model="goal.isCompleted" @click="clicked(goal.description)">
                </li>
                <li v-else> rien à voir ici</li>
            </ul>


            <div class="card-actions justify-end">
                <button class="btn btn-primary" @click="afficher">Afficher step goals</button>
            </div>
        </div>
    </div>

</template>


<script setup>
const props = defineProps({
    id: {
        type: String,
        required: true,
    },
    globalObjective: {
        type: String,
        required: true,
    },
    stepGoals: {
        type: Array,
        required: true,
    },
})

const emit = defineEmits({
    'click': (id) => {
        if (id) {
            return true;
        } else {
            console.log('id is required');
            console.warn('C\'est la catastrophe !!!!!!');
            console.error('ON A PAS DE ID Dans le event click');
            return false;
        }
    },
     'afficher': (id) => {
        if (id) {
            return true;
        } else {
            console.log('id is required');
            console.warn('C\'est la catastrophe !!!!!!');
            console.error('ON A PAS DE ID Dans le event afficher');
            return false;
        }
    }
})

function clicked(description){
    emit("click", description)
}

function afficher(description){
    emit("afficher", description);
}
</script>