<script lang="js">
// import Counter from './components/Counter-item.vue';
import Counter from "./components/Counter-item.vue"
export default {
  components: {
    Counter,
  }
  // data() {
  //   return {
  //     // These are interactive data properties:
  //     count: 0,
  //     counterTitle: 'Counter Standard',
  //     incrementAmount: 1,
  //     message: 'it works!',
  //     listOfNumbers: [1, 2, 3, 4, 5]
  //   }
  // },
  // computed: {
  //   displayTitle() {
  //     if (this.count < 20) {
  //       return 'Small Number title'
  //     } else {
  //       return 'Large number title'
  //     }
  //   }
  // },
  // methods: {
  //   incrementCount() {
  //     this.count += this.incrementAmount
  //   }
  // }
  // watch: {

  //   count(newValue) {
  //     // the normal paradigm:
  //     if(newValue > 20) {
  //       this.counterTitle += " Very long"
  //     }
  // // But using compute lets vue deturmine when its dependancies have changed.
  //     console.log(newValue)
  //   }
  // }
}
</script>

<template>
  <p>App.vue</p>
  <Counter />
  <!-- <div> -->
    <!-- <h1>{{ displayTitle }}</h1>
    <p>{{ count }}</p>
    <button v-on:click="incrementCount">incrememnt count</button>
    <div>
      <label for="incrementAmount">increment by:</label>
      <input type="number" v-model="incrementAmount" />
    </div>

    <hr />
    <p v-if="message.length % 2 === 0">Even: {{ message }}</p>
    <p v-else>Odd: {{ message.toUpperCase() }}</p>
    <ul>
      <li v-for="(number, index) in listOfNumbers" :key="`item-${index}`">{{ number }}</li>
    </ul> -->
  <!-- </div> -->
</template>
