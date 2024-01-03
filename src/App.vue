<template>
  <vue-tags-input
    ref="vueTagsInput" v-model="newTag" :tags="tags" :autocomplete-items="autocompleteItems"
    :placeholder="inputPlaceholder" :is-draggable="true"
    :allow-edit-tags="true" :autocomplete-min-length="autocompleteMinLength"
    @click="autocompleteMinLength = 0" @tags-changed="setNewTags" @tag-order-changed="newTagsOrder => tags = newTagsOrder"
  />
</template>

<script>
import { VueTagsInput } from '../dist/vue-tags-input'
// import VueTagsInput from './vue-tags-input.vue'

export default {
  name: 'App',
  components: { VueTagsInput },
  data () {
    return {
      newTag: '',
      tags: [],
      autocompleteItems: [
        { text: 'Dog', tag: 'dog' },
        { text: 'Cat', tag: 'cat' },
        { text: 'Lizard', tag: 'lizard' }
      ],
      tagInputFocus: false,
      inputPlaceholder: 'Start typing ...',
      autocompleteMinLength: 0
    }
  },
  methods: {
    setNewTags (newTags) {
      this.tags = newTags
      this.autocompleteMinLength = 1
    }
  }
}
</script>

<style>

</style>
