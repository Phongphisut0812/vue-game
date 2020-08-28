<template>
  <div>
      <button v-on:click="Start" class="button btn btn-warning" id="start">Start</button>
      <button v-on:click="Attack" class="button btn btn-warning" id="atk">Attack</button>
      <button v-on:click="Special" class="button btn btn-warning" id="atk">Special Attack</button>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      /*
      aplayer: { name: "kko", hp: 0, image: "0" },
      mmonster: { name: "ook", hp: 0, image: "g" },
      */
      
      player: [
        { name: "Iron man", hp: 280, image: require("../assets/ironman.png") },
        { name: "Thor", hp: 300, image: require("../assets/Thor.png") },
        { name: "Loki", hp: 200, image: require("../assets/Loki1.png") },
        { name: "Captain", hp: 280, image: require("../assets/Captain.png") },
        { name: "The Hulk", hp: 300, image: require("../assets/Hulk.png") },
      ],
      monster: [
        { name: "Thanos", hp: 300, image: require("../assets/Thanos1.png") },
        { name: "Black Dwarf", hp: 250, image: require("../assets/Black.png") },
        { name: "Corvus Glaive", hp: 200, image: require("../assets/Corvus.png") },
        { name: "Ebony maw", hp: 210, image: require("../assets/Ebony.png") },
        { name: "Proxi Midnight", hp: 240, image: require("../assets/Procxima.png") },
      ],
    };
  },

  methods: {
    randomNO: function (min, max) {
      return Math.max(Math.floor(Math.random() * max) + 1, min);
    },
    Start: function () {
      //1.random player 1-3
      //2.random monster 1-3
      this.aplayer = this.randomNO(1, 5) - 1; //{..}
      this.mmonster = this.randomNO(1, 5) - 1;

      this.name_player = this.player[this.aplayer].name;
      this.$emit("N_name", this.name_player);
      console.log("emit", this.name_player);
      this.hp_player = this.player[this.aplayer].hp;
      this.$emit("N_hp", this.hp_player);
      console.log("hp", this.hp_player);
      this.image_player = this.player[this.aplayer].image;
      this.$emit("N_image", this.image_player);
      console.log("im", this.image_player);

      this.name_monster = this.monster[this.mmonster].name;
      console.log("emit", this.name_monster);
      this.$emit("G_name", this.name_monster);
      this.hp_monster = this.monster[this.mmonster].hp;
      this.$emit("G_hp", this.hp_monster);
      this.image_monster = this.monster[this.mmonster].image;
      this.$emit("G_image", this.image_monster);
    },
    Attack: function () {
      this.at = this.randomNO(3, 10);
      this.$emit("P_at", this.at);
      console.log("Attack :", this.at);

      this.at = this.randomNO(3, 10);
      this.$emit("M_at", this.at);
      console.log("Atk back" ,this.at);
                                                        
    },
    Special: function () {
      this.A_atk = this.randomNO(10, 20);
      this.$emit("P_SATK", this.A_atk);
      console.log("Special Attack :", this.A_atk);

      this.A_atk = this.randomNO(10, 20);
      this.$emit("M_SPATK", this.A_atk);
      console.log("SPATK back", this.A_atk);
    },
  },
};
</script>

<style>
.button {
  border: none;
  color: white;
  padding: 10px 40 px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
}
</style>