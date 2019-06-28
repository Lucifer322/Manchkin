<template>
  <div id="app">
    <form action class="m-2">Введите имя игрока:</form>
    <input
      class="m-2"
      type="text"
      v-model="player"
      @keyup.enter="(!player.length) ? null : players.push(player); player=''"
    >

    <ul class="list-group">
      <li class="list-group-item" v-for="player of players" :key="player">
        <person :player="player" @close="removePlayer"></person>
      </li>
    </ul>
  </div>
</template>

<script>
import Person from "./Person.vue";

export default {
  name: "app",
  data() {
    return {
      player: "",
      players: []
    };
  },
  components: {
    person: Person
  },
  methods: {
    removePlayer(player) {
      this.players.splice(this.players.indexOf(player), 1);
    }
  }
};
</script>

<style scoped>
.m-2 {
  display: inline-block;
}
</style>