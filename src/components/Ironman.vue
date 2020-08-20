<template>
  <div>
    <p>
      HP playe {{random(0,3)}}
      {{player[random(0,3)-1].name}}
    </p>+ รูป
    <hr />
    name = {{aplayer.name}}
    hp = {{aplayer.hp}}
    image = {{aplayer.image}}
    <hr />
    <p>HP monster 150</p>+ รูป
    <button @click="Start()">Start</button>
    <button @click="Arrack()">Attack</button>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
        aplayer:{name:"", hp:0, image:'a'},
      player: [
        { name: "Iron man", hp: 90 ,image:'a' },
        { name: "Thor", hp: 150 ,image:'b' },
        { name: "Loki", hp: 200 ,image:'c'},
      ],
      monster: [
        { name: "Thanos", hp: 90 ,image:'d'},
        { name: "Black Dwarf", hp: 150 ,image:'e'},
        { name: "Corvus Glaive", hp: 200 ,image:'f'},
      ],
    };
  },

  methods: {
    random: function (min, max) {
      return Math.max(Math.floor(Math.random() * max) + 1, min);
    },
    Start: function () {
        //1.random player 1-3
        //2.random monster 1-3
        this.aplayer = this.player[this.random(1,3)-1] //{..}

    },
    Attack:function(){
        //1.player --> monster
        //2.player <-- monster
        //3.player.HP <=0 ===>!
        //4.monster.HP <=0 ===>!
        //5.END GAME

    },
  },
};
</script>

<style>
</style>