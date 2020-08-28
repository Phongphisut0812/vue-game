<template>
  <div id="app">
    <game
      @N_name="H_name"
      @N_hp="H_hp"
      @N_image="H_image"
      @G_name="M_name"
      @G_hp="M_hp"
      @G_image="M_image"
      @P_at="P_at"
      @M_at="M_at"
      @P_SATK="P_Satk"
      @M_SPATK="M_Satk"
    ></game>
    <div class="row">
      <div class="col-md-4">
        <h1>
          NAME : {{The_name}}
          <br />
          HP : {{het_hp}}
        </h1>
        <div>
          <img :src="L_img" alt class="img-fluid image" :width="het_hp + 'vw' " />
        </div>
      </div>
      <div class="col-md-4">
        <img src="./assets/vs.png" />
      </div>
      <div class="col-md-4">
        <h1>
          NAME : {{oon_name}}
          <br />
          HP : {{mon_hp}}
        </h1>
        <div>
          <img :src="G_img" alt class="img-fluid image" :width="mon_hp + 'vw' " />
        </div>
      </div>
    </div>

    <modal
      v-if="het_hp <= 0 && mon_hp > 0 && The_name != ''"
      @$reset="$reset"
      @reset="reset"
      @close="showModal = false"
    >
      <h1 slot="body">YOU LOUSE</h1>
    </modal>

    <modal
      v-if="mon_hp <= 0 && het_hp > 0 && The_name != ''"
      @$reset="$reset"
      @reset="reset"
      @close="showModal = false"
    >
      <h1 slot="body">YOU WIN</h1>
    </modal>

    <modal
      v-if="(het_hp<=0 && mon_hp <= 0 ) && The_name != ''"
      v-bind="reset"
      @$reset="$reset"
      @reset="reset"
      @close="showModal = false"
    >
      <h1 slot="body">DRAW</h1>
    </modal>
  </div>
</template>

<script>
import modal from "./components/check";
import game from "./components/game.vue";
export default {
  name: "App",
  components: {
    modal,
    game,
  },
  data: function () {
    return {
      The_name: "",
      oon_name: "",
      het_hp: 0, 
      mon_hp: 0,
      attack: 0,
      L_img: "",
      G_img: "",
    };
  },
  methods: {
    H_name(value) {
      this.The_name = value;
      console.log("emit", this.The_name);
    },
    H_hp(value) {
      this.het_hp = value;
      console.log("emit", this.het_hp); 
    },
    H_image(value) {
      this.L_img = value;
      console.log("emit", this.L_img);
    },
    //monster
    M_name(value) {
      this.oon_name = value;
    },
    M_hp(value) {
      this.mon_hp = value;
    },
    M_image(value) {
      this.G_img = value;
    },
    //attack hero
    P_at(value) {
      this.attack = value;
      this.mon_hp -= this.attack;
      console.log("emit", this.mon_hp);
    },
    P_Satk(value) {
      this.attack = value;
      this.mon_hp -= this.attack;
    },
    //attack monster
    M_at(value) {
      this.attack = value;
      this.het_hp -= this.attack;
    },
    M_Satk(value) {
      this.attack = value;
      this.het_hp -= this.attack;
    },
    $reset(value) {
      this.The_name = value;
      this.oon_name = value;
      this.h_img = value;
      this.m_img = value;
    },
    reset(value) {
      this.het_hp = value;
      this.mon_hp = value;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #ffffff;
}
 
</style>
