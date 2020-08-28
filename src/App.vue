<template>
  <div id="app">
    <game
      @H_name="h_name"
      @H_hp="h_hp"
      @H_image="h_image"
      @M_name="m_name"
      @M_hp="m_hp"
      @M_image="m_image"
      @P_atk="p_atk"
      @M_atk="m_atk"
      @P_SATK="p_satk"
      @M_SPATK="m_satk"
    ></game>
    <div class="row">
      <div class="col-md-4">
        <h1>NAME :{{he_name}} <br> HP : {{he_hp}}</h1>
        <div>
          <img :src="h_img" alt class="img-fluid image" :width="he_hp + 'vw' " />
        </div>
      </div>
      <div class="col-md-4">
        <img src ="./assets/vs.png"  />
      </div>
      <div class="col-md-4">
        <h1>NAME :{{mon_name}} <br> HP : {{mon_hp}}</h1>
        <div>
          <img :src="m_img" alt class="img-fluid image" :width="mon_hp + 'vw' " />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import game from "./components/game.vue";
export default {
  name: "App",
  components: {
    game,
  },
  data: function () {
    return {
      he_name: "",
      mon_name: "",
      he_hp: 0,
      mon_hp: 0,
      attack: 0,
      h_img: "",
      m_img: "",
    };
  },
  methods: {
    h_name(value) {
      this.he_name = value;
      console.log("emit", this.he_name);
    },
    h_hp(value) {
      this.he_hp = value;
      console.log("emit", this.he_hp);
    },
    h_image(value) {
      this.h_img = value;
      console.log("emit", this.h_img);
    },
    //monster
    m_name(value) {
      this.mon_name = value;
    },
    m_hp(value) {
      this.mon_hp = value;
    },
    m_image(value) {
      this.m_img = value;
    },
    //attack hero
    p_atk(value) {
      this.attack = value;
      this.mon_hp -= this.attack;
      console.log("emit", this.mon_hp);
    },
    p_satk(value) {
      this.attack = value;
      this.mon_hp -= this.attack;
    },
    //attack monster
    m_atk(value) {
      this.attack = value;
      this.he_hp -= this.attack;
    },
    m_satk(value) {
      this.attack = value;
      this.he_hp -= this.attack;
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
.playGameScreen {
  background-image: url("");
  background-repeat: no-repeat;
  background-size: 100% 100%;
  height: 100vh;
}
</style>
