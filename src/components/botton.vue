<template>
  <div id="gee">
    <div class="row">
      <div class="col-sm">
        <p style="font-size: 150%">{{aplayer.name}}</p>
        <p>
          <img v-bind:style="{width: aplayer.hp + 'px'}" :src="hp1" alt height="20px" />
        </p>
        <p style="font-size: 150%">{{thp}}{{aplayer.hp}}</p>
        <p>
          <img style="width:90%" :src="aplayer.image" />
        </p>
      </div>
      <div class="row">
      <div class="col"></div>
      <div class="col"></div>
    </div>
      <div class="col-sm">
        <div class="row">
          <div class="col">
            <button class="btn btn-primary" @click="start()" style="border-radius:30px;">เริ่ม</button></div>
          <div class="col">
            <button v-bind:disabled="end" class="btn btn-danger" @click="attack()"  style="border-radius:30px;">โจมตี</button></div>
          <div class="col">
            <button v-bind:disabled="end" class="btn btn-dark" @click="special()"  style="border-radius:30px;">โจมตีพิเศษ</button></div>
          <div class="col">
            <button class="btn btn-light" @click="reset()"  style="border-radius:30px;">เล่นอีกครั้ง</button></div>
          <br />
          <img src="http://www.pngmart.com/files/11/Versus-PNG-Clipart.png"
            width="100%"
          />
        </div>
        <div class="row">
          <div class="col-sm"></div>
          <div class="col-sm">
            <div id="score">
              <div v-if="amonster.hp <= 0"><FONT COLOR=black>คุณชนะ</FONT></div>
              <div v-else-if="aplayer.hp <= 0"><FONT COLOR=black>คุณแพ้</FONT></div>
            </div>
          </div>
          <div class="col-sm"></div>
        </div>
      </div>
      <div class="col-sm">
        <p style="font-size: 150%">{{amonster.name}}</p>
        <p><img v-bind:style="{width: amonster.hp + 'px'}" :src="hp2" alt height="15px" /></p>
        <p style="font-size: 150%">{{thp}}{{amonster.hp}}</p>
        <p><img style="width:90%" :src="amonster.image" /></p>
      </div>
    </div>
    <hr />
  </div>
</template>
<script>
export default {
  data: function () {
    return {
      thp: "HP:",
      end: false,
      hp2:
        "https://i.ppy.sh/bca61e3c2183a86ddb4c1d75914fab845e2b128f/687474703a2f2f692e696d6775722e636f6d2f6953766c5662432e706e67",
      hp1:
        "https://i.ppy.sh/bca61e3c2183a86ddb4c1d75914fab845e2b128f/687474703a2f2f692e696d6775722e636f6d2f6953766c5662432e706e67",
      aplayer: { name: "", hp: 1, image: "", hp1: "" },
      player: [
        {name: "Mew",hp: 500,image:
            "https://vignette.wikia.nocookie.net/nintendo/images/b/bf/Mew.png/revision/latest?cb=20180612225527&path-prefix=en",
        },
        {name: "Piplup",hp: 350,image:
            "https://th.portal-pokemon.com/play/resources/pokedex/img/pm/f3868a6a16c75d75435819deab8bab97926fc54c.png",
        },
        {name: "Espeon",hp: 400,image:
            "https://th.portal-pokemon.com/play/resources/pokedex/img/pm/c2d8c73ae839798f984fb381043ff9b274a03406.png",
        },
        {name: "Rocon",hp: 300,image:
            "https://th.portal-pokemon.com/play/resources/pokedex/img/pm/89719dbcbddd11a1e6bc5f4366e00910a04eaf9f.png",
        },
        {name: "Pikachu",hp: 450,image: 
            "https://th.portal-pokemon.com/play/resources/pokedex/img/pm/2b3f6ff00db7a1efae21d85cfb8995eaff2da8d8.png",
        },
      ],
      amonster: { name: "", hp: 1, image: "", hp1: "" },
      monster: [
        {name: "Kirlia",hp: 350,image:
            "https://th.portal-pokemon.com/play/resources/pokedex/img/pm/581324fb829bc344584a92e7443b759146fdeda0.png",
        },
        {name: "Greninja",hp: 400,image:
            "https://www.pngkit.com/png/full/154-1544576_greninja-transparent-svg-transparent-stock-.png",
        },
        {name: "Meowth",hp: 300,image:
            "https://th.portal-pokemon.com/play/resources/pokedex/img/pm/6ea01871238908780334293e6407033650d803a9.png",
        },
        {name: "Jirashi",hp: 500,image: 
            "https://th.portal-pokemon.com/play/resources/pokedex/img/pm/03c12c7894da033493007adcef4c9ac650a23cd8.png",
        },
        {name: "Thunder",hp: 450,image: 
            "https://th.portal-pokemon.com/play/resources/pokedex/img/pm/427bb0b94b44ff442449cfba55dc6829df76891c.png",
        },
      ],
      player_max: "",
      monster_max: "",
    };
  },
  methods: {
    randomno: function (min, max) {
      return Math.max(Math.floor(Math.random() * max) + 1, min);
    },
    start: function () {
      this.aplayer = this.player[this.randomno(1, 5) - 1];
      this.amonster = this.monster[this.randomno(1, 6) - 1];
    },
    attack: function () {
      this.player_max = Math.floor(Math.random() * 7 + 3);
      this.amonster.hp = this.amonster.hp - this.player_max;
      this.monster_max = Math.floor(Math.random() * 10 + 3);
      this.aplayer.hp = this.aplayer.hp - this.monster_max;
      if (this.aplayer.hp <= 0) {
        this.aplayer.hp = 0;
        this.end = true;
      } else if (this.amonster.hp <= 0) {
        this.amonster.hp = 0;
        this.end = true;
      }
    },
    special: function () {
      this.player_max = Math.floor(Math.random() * 20 + 6);
      this.amonster.hp = this.amonster.hp - this.player_max;
      this.monster_max = Math.floor(Math.random() * 13 + 6);
      this.aplayer.hp = this.aplayer.hp - this.monster_max;
      if (this.aplayer.hp <= 0) {
        this.aplayer.hp = 0;
        this.end = true;
      } else if (this.amonster.hp <= 0) {
        this.amonster.hp = 0;
        this.end = true;
      }
    },
    reset: function () {
      window.location.reload();
    },
  },
};
</script>
<style>
#score {
  font-size: 500%;
  color: aliceblue;
}
#gee{
  width: 100%;
  border-radius: 50px;
  background-color: #82E0AA;
  box-shadow: 0 4px 18px 0 rgba(0, 0, 0, 0.2), 0 8px 20px 0 rgba(0, 0, 0, 0.19);
}

</style>