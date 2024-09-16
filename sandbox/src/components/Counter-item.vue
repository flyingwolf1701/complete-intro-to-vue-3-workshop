<script>
export default {
    // This is basically like initial state in redux. 
    data: () => ({
        count: 0,
        counterTitle: 'Counter Standard',
        incrementAmount: 8,
    }),
    // computed cannot have side effects (like redux), if it has a side effect it can run a method or watch is a function based on an event or a change that can have a side effect. 
    computed:{
      displayTitle() {
        if (this.count < 20) {
          return "Small Number title"
        } else {
          return 'Large number title'
        }
      },
      optimisedIncrementalAmount() {
        return this.displayTitle.length * this.incrementAmount
      }
    },
    // watch is a function based on an event that can have side effects. 
    // methods are functions 
    methods: {
      incrementCount() {
        this.count += this.incrementAmount
      },
    },
}
</script>

<template>
    <div >
      <p>Counter-item</p>
        <h1>{{ displayTitle}}</h1>
        <p>{{ count }}</p>
        <button v-on:click="incrementCount">incrememnt count</button>
        <div>
          <label for="incrementAmount">increment by:</label>
          <input 
            type="number" 
            v-model="incrementAmount"
          >
        </div>
  
        <hr/>
        <p v-if="message.length % 2 === 0">Even: {{message}} </p>
        <p v-else>Odd: {{message.toUpperCase()}} </p>
        <ul>
          <li v-for="(number, index) in listOfNumbers" :key="`item-${index}`">{{number}}</li>
        </ul>
      </div>
  </template>