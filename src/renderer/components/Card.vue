<template>
    <div class="dropdown">
        <button id="dropdown-open" class="card">{{this.name}}</button>
        <div id="dropdown-content" class="dropdown-content">
            <button @click="onClick" class="dropdown-content-item-red" v-for="card in cards">{{card.name}}</button>
            <button @click="onClick2" class="dropdown-content-item-black" v-for="card in cards2">{{card.name}}</button>
            <button @click="onClick3" class="dropdown-content-item-rebeccapurple" v-for="card in cards3">{{card.name}}
            </button>
            <button @click="onClick4" class="dropdown-content-item-blue" v-for="card in cards4">{{card.name}}</button>
            <button @click="onClick5" class="dropdown-content-item" v-for="card in cards5">{{card.name}}</button>
        </div>
    </div>
</template>

<script>
  export default {
    props: ['index', 'name', 'type'],
    data () {
      return {
        cards: [{
          name: '♥️A',
          value: 514
        }, {
          name: '♥️2',
          value: 502
        }, {
          name: '♥️3',
          value: 503
        }, {
          name: '♥️4',
          value: 504
        }, {
          name: '♥️5',
          value: 505
        }, {
          name: '♥️6',
          value: 506
        }, {
          name: '♥️7',
          value: 507
        }, {
          name: '♥️8',
          value: 508
        }, {
          name: '♥️9',
          value: 509
        }, {
          name: '♥️10',
          value: 510
        }, {
          name: '♥️J',
          value: 511
        }, {
          name: '♥️Q',
          value: 512
        }, {
          name: '♥️K',
          value: 513
        }
        ],
        cards2: [{
          name: '♠️A',
          value: 414
        }, {
          name: '♠️2',
          value: 402
        }, {
          name: '♠️3',
          value: 403
        }, {
          name: '♠️4',
          value: 404
        }, {
          name: '♠️5',
          value: 405
        }, {
          name: '♠️6',
          value: 406
        }, {
          name: '♠️7',
          value: 407
        }, {
          name: '♠️8',
          value: 408
        }, {
          name: '♠️9',
          value: 409
        }, {
          name: '♠️10',
          value: 410
        }, {
          name: '♠️J',
          value: 411
        }, {
          name: '♠️Q',
          value: 412
        }, {
          name: '♠️K',
          value: 413
        }
        ],
        cards3: [{
          name: '♦️A',
          value: 314
        }, {
          name: '♦️2',
          value: 302
        }, {
          name: '♦️3',
          value: 303
        }, {
          name: '♦️4',
          value: 304
        }, {
          name: '♦️5',
          value: 305
        }, {
          name: '♦️6',
          value: 306
        }, {
          name: '♦️7',
          value: 307
        }, {
          name: '♦️8',
          value: 308
        }, {
          name: '♦️9',
          value: 309
        }, {
          name: '♦️10',
          value: 310
        }, {
          name: '♦️J',
          value: 311
        }, {
          name: '♦️Q',
          value: 312
        }, {
          name: '♦️K',
          value: 313
        }],
        cards4: [{
          name: '♣️A',
          value: 214
        }, {
          name: '♣️2',
          value: 202
        }, {
          name: '♣️3',
          value: 203
        }, {
          name: '♣️4',
          value: 204
        }, {
          name: '♣️5',
          value: 205
        }, {
          name: '♣️6',
          value: 206
        }, {
          name: '♣️7',
          value: 207
        }, {
          name: '♣️8',
          value: 208
        }, {
          name: '♣️9',
          value: 209
        }, {
          name: '♣️10',
          value: 210
        }, {
          name: '♣️J',
          value: 211
        }, {
          name: '♣️Q',
          value: 212
        }, {
          name: '♣️K',
          value: 213
        }],
        cards5: [{
          name: '大王',
          value: 999
        }, {
          name: '小王',
          value: 998
        }]
      }
    },

    methods: {
      onClick: function (value) {
        let result = {}
        for (let i = 0; i < this.cards.length; i++) {
          if (this.cards[i].name === value.target.innerText) {
            result = this.cards[i]
            break
          }
        }
        this.$parent.onClick(result, this.index, this.type)
      },
      onClick2: function (value) {
        let result = {}
        for (let i = 0; i < this.cards2.length; i++) {
          if (this.cards2[i].name === value.target.innerText) {
            result = this.cards2[i]
            break
          }
        }
        this.$parent.onClick(result, this.index, this.type)
      },
      onClick3: function (value) {
        let result = {}
        for (let i = 0; i < this.cards3.length; i++) {
          if (this.cards3[i].name === value.target.innerText) {
            result = this.cards3[i]
            break
          }
        }
        this.$parent.onClick(result, this.index, this.type)
      },
      onClick4: function (value) {
        let result = {}
        for (let i = 0; i < this.cards4.length; i++) {
          if (this.cards4[i].name === value.target.innerText) {
            result = this.cards4[i]
            break
          }
        }
        this.$parent.onClick(result, this.index, this.type)
      },
      onClick5: function (value) {
        let result = {}
        for (let i = 0; i < this.cards5.length; i++) {
          if (this.cards5[i].name === value.target.innerText) {
            result = this.cards5[i]
            break
          }
        }
        this.$parent.onClick(result, this.index, this.type)
      }
    }

  }
</script>

<style scoped>
    .card {
        font-size: 14px;
        cursor: pointer;
        width: 50px;
        height: 70px;
    }

    .dropdown {
        position: relative;
        display: inline-block;
    }

    .dropdown-content {
        z-index: 10000;
        display: none;
        position: absolute;
        background-color: #f9f9f9;
        min-width: 340px;
        box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
    }

    .dropdown-content-item {
        width: 55px;
        height: 30px;
    }

    .dropdown-content-item-blue {
        width: 55px;
        height: 30px;
        background: darkblue;
        color: white;
    }

    .dropdown-content-item-rebeccapurple {
        width: 55px;
        height: 30px;
        background: rebeccapurple;
        color: white;
    }

    .dropdown-content-item-red {
        width: 55px;
        height: 30px;
        background: red;
        color: white;
    }

    .dropdown-content-item-black {
        width: 55px;
        height: 30px;
        background: black;
        color: white;
    }

    #dropdown-content:hover {
        display: block;
    }

    #dropdown-open:focus + #dropdown-content {
        display: block;
    }

</style>
