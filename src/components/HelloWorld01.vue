<script setup lang="ts">
import { ref, reactive } from 'vue'

defineProps<{ msg: string }>()

const characters = reactive([
  { name: 'Gon Freecss', type: 'Enhancer' },
  { name: 'Killua Zoldyck', type: 'Transmuter'}
])
const newCharacterName = ref(null)
const newCharacterType = ref(null)

const addCharacter = () => {
  if (!newCharacterName.value || !newCharacterType.value) {
    return
  }
  characters.push({
    name: newCharacterName.value,
    type: newCharacterType.value
  })
}
</script>

<template>
  <h1>{{ msg }}</h1>

  <div class="card">
    <ul>
      <li v-for="character in characters">
        {{ character.name }}は{{ character.type }}です。
      </li>
    </ul>
    <input type="text" v-model="newCharacterName"/>
    <input type="text" v-model="newCharacterType"/>
    <input type="button" v-on:click="addCharacter" value="追加する" />
    <p>
      Edit
      <code>components/HelloWorld.vue</code> to test HMR
    </p>
  </div>

  <p>
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank"
      >create-vue</a
    >, the official Vue + Vite starter
  </p>
  <p>
    Install
    <a href="https://github.com/vuejs/language-tools" target="_blank">Volar</a>
    in your IDE for a better DX
  </p>
  <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
