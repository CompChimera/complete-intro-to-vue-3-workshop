<script>

export default {
  props: {
    charactersList: {
      type: Array,
      required: true 
    },
    newCharacter: {
      type: Object,
      required: true 
    },
  },
  emits: ['add-new-character']
}
</script>

<template>
  <h2>New Character</h2>
<div class="new-char__wrapper" style="padding: 20px; border: 1px solid black'">
  <label for="character-name">Name: </label>
  <input
    type="text"
    v-model="newCharacter.name"
    placeholder="Name"
    required
    @keyup.enter="$emit('add-new-character')"
  />
  <br/>
  <label for="character-bio">Bio: </label>
  <input
    type="text"
    v-model="newCharacter.bio"
    placeholder="Character Background"
  />
  <br/>
  <label for="character-powers" class="disabled">Powers - disabled: </label>
  <br/>
  <fieldset class="disabled" style="max-width: 400px">      
        <legend>Character Powers - disabled</legend>      
        <input disabled type="checkbox" name="character_power" value="strength">Strength<br>      
        <input disabled type="checkbox" name="character_power" value="cunning">Cunning<br>      
        <input disabled type="checkbox" name="character_power" value="friendship">Friendship<br>      
        <input disabled type="checkbox" name="character_power" value="famous">Famous<br>          
    </fieldset>   
  <!-- @keyup.enter="$emit('add-new-character')" -->
  <button @click="$emit('add-new-character')" style="margin-top: 20px;">Add new character</button>
</div>
</template>