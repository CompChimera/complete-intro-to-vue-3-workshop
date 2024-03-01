<script>
export default {
  props: {
    character: {
      type: Object,
      required: true
    }
  },
  emits: ['favourite'],
  methods: {
    favouriteCharacter() {
          this.$emit('favourite', this.character)
        },
    }
}
</script>

<template>
  <div>
      <span v-for="(value, key) in character" :key="`characterslist-detail-${key}-${value}`" style="padding-left: 10px;">
        <span style="font-weight: bold">{{ key[0].toUpperCase() + key.substring(1) }}</span> : {{ value }} 
      </span>
      <button style="margin-left: 20px; margin-top: 20px;" @click="favouriteCharacter"> ⭐ Favorite </button>
    </div>
</template>