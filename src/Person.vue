<template>
  <div>
    <div>
      {{player}}: level:
      <span style="color: red">
        <button @click="sub">-</button>
        <strong>{{lvl}}</strong>
        <button @click="add">+</button>
      </span>
      <span @click="sexBoolean = !sexBoolean">sex: {{sexBoolean ? 'F' : 'M'}}</span>
      <span class="close" @click="close">x</span>
    </div>
  </div>
</template>

<script>
export default {
  props: ["player"],
  data() {
    return {
      lvl: 1,
      sexBoolean: false
    };
  },
  methods: {
    add() {
      this.lvl++;
      if (this.lvl === 10) {
        alert(`${this.player} победил`);
        location.reload();
      }
    },
    sub() {
      if (this.lvl === 1) return;
      this.lvl--;
    },
    close() {
      this.$emit("close", this.player);
    }
  }
};
</script>

<style >
body {
  font-size: 25px;
  user-select: none;
}
button {
  border: none;
  background: white;
  font-size: 18px;
  outline: none;
}
</style>