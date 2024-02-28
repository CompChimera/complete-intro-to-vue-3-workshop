<script>
export default {
  props: {
    charactersList: {
      type: Array,
      required: true 
    },
    favouriteList: {
      type: Array,
      required: true 
    }
  },
  methods: {
      favouriteFlag(favouriteAdd, event) {
            this.favouriteList.push(favouriteAdd);
        },
    }
}
</script>

<template>
  <h2 v-if="charactersList.length > 0">Main Characters: </h2>
  <h2 v-else>Characters: To be announced!</h2>
  <ul>
    <li v-if="charactersList.length > 0" v-for="(character, index) in charactersList" :key="`character-${index}`">
      <span v-for="(value, key) in character" :key="`characterslist-detail-${key}-${value}`" style="padding-left: 10px;">
        <span style="font-weight: bold">{{ key[0].toUpperCase() + key.substring(1) }}</span> : {{ value }} 
      </span>
      <button @click="favouriteFlag(character, $event)" style="margin-left: 20px; margin-top: 20px;"> ⭐ Favorite </button>
    </li>
  </ul>
</template>