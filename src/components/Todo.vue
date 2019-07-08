<template>
  <div>
    <form @submit.prevent="addHeroes">
      <input type="text" v-model="hero" />
      <button type="submit" v-show="!updateSubmit">add</button>
      <button type="button" v-show="updateSubmit" @click="updateHeroes(hero)">Update Kak</button>
    </form>
    <ul>
      <li v-for="list in heroes" :key="list.id">
          {{ list }}
          - <a href="#lol" @click="removeHeroes(list)">🔥 Remove</a>
          - <a href="#lol" @click="editHeroes(list)">📌 Edit</a>
      </li>
    </ul>
  </div>
</template>


<script>
export default {
  name: "todo",
  data() {
    return {
      heroes: ["Queen Of Pain", "Crystal Mayden", "Lycan"],
      hero: "",
      updateSubmit: false,
    };
  },
  methods: {
    addHeroes() {
      this.heroes.push(this.hero);
      this.hero = "";
    },
    removeHeroes(hero){
        const index = this.heroes.indexOf(hero)
        this.heroes.splice(index,1)
    },
    editHeroes(heroes){
        this.hero = heroes
        this.updateSubmit = true
    },
    updateHeroes(hero){
        const index = this.heroes.indexOf(hero)
        if(index !== -1){
            this.heroes[index] == hero
        }
        this.updateSubmit = false
    }
  }
};
</script>
