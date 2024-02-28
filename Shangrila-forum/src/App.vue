<script >
import CharacterList from './components/CharacterList.vue'


export default {
    data: () => ({
        // charactersList: [
        //     { name: 'Rakuro', bio: 'In game name - Sunraku', powers: ['speed', 'strength'] },
        //     { name: 'Towa', bio: 'In game name: Authur Pencilgon', powers: ['strength', 'friendship'] },
        //     { name: 'Rei', bio: 'In game name: Psyger-0', powers: ['strength   ', 'speed', 'cunning'] },
        //     { name: 'Kei', bio: 'In game name: Oikatzo', powers: ['cunning', 'speed', 'famous'] }
        // ],
        charactersList: [],
        newCharacter: {
            name: ''
        },
        favouriteList: []
    }),
    computed: {
        powerStatistics() {
            const powers = ['strength', 'cunning', 'friendship', 'famous'];
            const statistics = {
                strength: 0,
                cunning: 0,
                friendship: 0,
                famous: 0
            };
            this.charactersList.forEach(character => {
                powers.forEach(power => {
                    if (character.powers && character.powers.indexOf(power) > -1) {
                        statistics[power] += 1;
                    }
                });
            });
            return statistics;
        }
    },
    methods: {

        addNewCharacter() {
            this.charactersList.push(this.newCharacter);
            this.newCharacter = { name: '' };
        }
    },
    components: { CharacterList }
}
</script>

<template>
 <h2>Statistics</h2>

<ul>
  <li v-for="(stat, type) in powerStatistics" :key="`character-${stat}-${type}`"> <span>{{ type[0].toUpperCase() + type.substring(1) }} : {{ stat }} </span></li>
</ul>
<CharacterList :charactersList="charactersList" :favouriteList="favouriteList"/>

<h2>New Character (Limited to names)</h2>
<div class="new-char__wrapper" style="padding: 20px; border: 1px solid black'">
  <label for="character-name">Name: </label>
  <input
    type="text"
    v-model="newCharacter.name"
    @keyup.enter="addNewCharacter"
  />
</div>
<div class="list-wrapper" 
style="display: flex; flex-direction: column; max-width: 500px; gap: 20px;">
  <div class="char-list" style="background-color: #d3d3d3; padding: 10px;">
    <span style="font-weight: bold;">List of Characters:</span>
    <p>
      <span v-for="(character, index) in charactersList" :key="`listing-character-${index}`">
         {{ character.name }}{{ index === charactersList.length - 1 ? '' : ', ' }} 
        </span>
    </p>
  </div>
  <div class="fav-list" style="background-color: #d3d3d3; padding: 10px;">
    <span style="font-weight: bold;">List of Favourite Characters:</span>
    <p>
      <span v-if="favouriteList.length > 0" v-for="(character, index) in favouriteList" :key="`fav-character-${index}`">
         {{ character.name }}{{ index === favouriteList.length - 1 ? '' : ', ' }} 
        </span>
        <span v-else>There are no favourites :( </span>
    </p>
  </div>
</div> <!-- End List wrapper-->
</template>
