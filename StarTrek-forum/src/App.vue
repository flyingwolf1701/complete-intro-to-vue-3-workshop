<script>
export default {
  data() {
    return {
      showTitle: 'Star Trek: TNG',
      showFavorites: false,
      totalChar: 0,
      human: 0,
      newCharacter: {
        name: '',
        role: '',
        species: '',
        faction: '',
        alignment: '',
        favorite: false
      },

      characterList: [
        {
          name: 'Jean-Luc Picard',
          role: 'Captain',
          species: 'Human',
          faction: 'Federation',
          alignment: 'Lawful Good',
          favorite: false
        },
        {
          name: 'William Riker',
          role: 'Commander',
          species: 'Human',
          faction: 'Federation',
          alignment: 'Neutral Good',
          favorite: false
        },
        {
          name: 'Data',
          role: 'Android Officer',
          species: 'Android',
          faction: 'Federation',
          alignment: 'Neutral Good',
          favorite: false
        },
        {
          name: 'Worf',
          role: 'Security Officer',
          species: 'Klingon',
          faction: 'Federation',
          alignment: 'Lawful Neutral',
          favorite: false
        },
        {
          name: 'Geordi La Forge',
          role: 'Chief Engineer',
          species: 'Human',
          faction: 'Federation',
          alignment: 'Neutral Good',
          favorite: false
        },
        {
          name: 'Deanna Troi',
          role: 'Counselor',
          species: 'Betazoid',
          faction: 'Federation',
          alignment: 'Neutral Good',
          favorite: false
        },
        {
          name: 'Beverly Crusher',
          role: 'Chief Medical Officer',
          species: 'Human',
          faction: 'Federation',
          alignment: 'Neutral Good',
          favorite: false
        },
        {
          name: 'Guinan',
          role: 'Bartender',
          species: 'El-Aurian',
          faction: 'Federation',
          alignment: 'Neutral Good',
          favorite: false
        }
      ],
      favoritesList: []
    }
  },
  computed: {
    numChar() {
      return this.characterList.length
    },
    numHumans() {
      return this.characterList.filter(
        (character) => character.species === 'Human'
      ).length
    },
    percentageHuman() {
      return (this.numHumans / this.numChar) * 100
    }
  },
  methods: {
    addNewCharacter() {
      this.characterList.push(this.newCharacter)
      this.newCharacter = {
        name: '',
        role: '',
        favorite: false
      }
    },
    toggleShowFavorite() {
      this.showFavorites = !this.showFavorites
      console.log('show favorites:', this.showFavorites)
    },
    toggleCharFavorite(character) {
      this.favoritesList.push(character.name)
      console.log('favoriteslist', this.favoritesList)
    }
  }
}
</script>

<template>
  <div id="app">
    <div>
      <button v-if="!showFavorites" v-on:click="toggleShowFavorite">show favorites</button>
      <button v-else v-on:click="toggleShowFavorite">hide favorites</button>

      <ul v-if="showFavorites && favoritesList.length >= 1">
        <li v-for="(character, index) in favoritesList" :key="`favChar=${index}`">
          {{ character }}
        </li>
      </ul>
      <p v-if="showFavorites && favoritesList.length < 1">No characters added to favorites</p>
    </div>
    <hr />

    <p v-if="!characterList.length">No characters exist</p>
    <ul v-else>
      <li v-for="(character, index) in characterList" :key="`char-${index}`">
        {{ character.role }}: {{ character.name }} -- {{ character.favorite }}
        <button v-if="character.favorite" @click="toggleCharFavorite(character)">Favorited</button>
        <button v-else @click="toggleCharFavorite(character)">Like</button>
      </li>
    </ul>
    <div>
      <h2>Percentage of Characters that are human: {{ percentageHuman }}%</h2>
      <p>Total Characters: {{ numChar }}</p>
      <p>Humans: {{ numHumans }}</p>
    </div>
    <hr />
    <div>
      <h2>Add new Character</h2>

      <label for="name">name</label>
      <input type="text" v-model="newCharacter.name" />
      <label for="role">rank/role</label>
      <input type="text" v-model="newCharacter.role" @keyup.enter="addNewCharacter" />

      <pre>{{ newCharacter }}</pre>
    </div>
  </div>
</template>
