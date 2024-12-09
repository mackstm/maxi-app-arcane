<template>
    <div class="container">
        <div class="row">
            <div class="card col-12 col-lg-6">
                <div class="card-header">
                    <h1 class="text-success">Add Character</h1>
                </div>
                <div class="card-body">
                    <form @submit.prevent="addCharacter">
                        <div class="form-group">
                            <label for="name">Name</label>
                            <input type="text" class="form-control" id="name" v-model="name" placeholder="Enter character name"/>
                        </div>
                        <div class="form-group">
                            <label for="origin">Origin</label>
                            <input type="text" class="form-control" id="origin" v-model="origin" placeholder="Enter character origin"/>
                        </div>
                        <div class="form-group">
                            <label for="ability">Special ability</label>
                            <input type="text" class="form-control" id="ability" v-model="ability" placeholder="Enter special ability"/>
                        </div>
                        <div class="form-group">
                            <label for="allies">Allies</label>
                            <input type="text" class="form-control" id="allies" v-model="allies" placeholder="Enter allies separated by commas"/>
                        </div>
                        <div class="form-group">
                            <div>
                                <label for="mission">Mission Accomplished</label>
                            </div>

                            <input type="checkbox" class="form-check-input" id="mission" v-model="mission"/>
                            <label class="form-check-label" for="mission">Yes</label>
                        </div>

                        <button type="submit" class="btn btn-success mt-2">Add</button>
                    </form>
                </div>
            </div>

            <div class="card col-12 col-lg-6">
                <div class="card-header">
                    <h1 class="text-warning">Characters</h1>
                </div>

                <div class="card-body">
                    <table class="table table-striped table-warning">
                        <thead>
                            <tr>
                                <th>Name</th>
                                <th>Origin</th>
                                <th>Ability</th>
                                <th>Allies</th>
                                <th>Mission Accomplished</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr v-for="charac in characters" :key="charac.name">
                                <td>{{ charac.name }}</td>
                                <td>{{ charac.origin }}</td>
                                <td>{{ charac.ability }}</td>
                                <td>{{ charac.allies.join(', ') }}</td>
                                <td>{{ charac.mission ? 'Yes' : 'No' }}</td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';

    
    const characters = ref([]);

    const name = ref('');
    const origin = ref('');
    const ability = ref('');
    const allies = ref([]);
    const mission = ref(false);

    const addCharacter = () => {
        const newCharacter = {
            name: name.value,
            origin: origin.value,
            ability: ability.value,
            allies: allies.value.split(',').map(ally => ally.trim()),
            mission: mission.value
        };

        characters.value.push(newCharacter);

        resetForm();
    }

    const resetForm = () => {
        name.value = '';
        origin.value = '';
        ability.value = '';
        allies.value = [];
        mission.value = false;
    }

</script>

<style lang="scss" scoped>

</style>