<template>
    <div id="wrapper">
        <main>
            <!-- 其他玩家 -->
            <div style="display: inline-flex; width: 100%;">
                <div>
                    <div>左方游戏区域</div>
                    <div>
                        <div>
                            <card :index="index" :name="card.name" :type="1" :key="index"
                                  v-for="(card, index) in cards">
                                {{card.name}}
                            </card>
                        </div>
                        <div>
                            <card :index="index" :name="card.name" :type="2" :key="index"
                                  v-for="(card, index) in cards2">
                                {{card.name}}
                            </card>
                        </div>
                        <div>
                            <card :index="index" :name="card.name" :type="3" :key="index"
                                  v-for="(card, index) in cards3">
                                {{card.name}}
                            </card>
                        </div>
                    </div>
                    <button style="width: 80px; height: 30px; margin-top: 30px;" @click="resetLeft">重置</button>
                </div>
                <!-- 右边玩家 -->
                <div style="margin-left: 100px">
                    <div style="margin-left: 110px">右方游戏区域</div>
                    <div>
                        <card :index="index" :name="card.name" :type="4" :key="index" v-for="(card, index) in cards4">
                            {{card.name}}
                        </card>
                    </div>
                    <div>
                        <card :index="index" :name="card.name" :type="5" :key="index" v-for="(card, index) in cards5">
                            {{card.name}}
                        </card>
                    </div>
                    <div>
                        <card :index="index" :name="card.name" :type="6" :key="index" v-for="(card, index) in cards6">
                            {{card.name}}
                        </card>
                    </div>
                    <button style="width: 80px; height: 30px; margin-top: 30px;" @click="resetRight">重置</button>
                </div>
            </div>
            <!-- 自己 -->
            <div style="width: 80%; position: absolute; top:430px;">己方游戏区域</div>
            <div style="width: 80%; position: absolute; top:450px; display: inline-flex;">
                <div>
                    <div>
                        <card :index="index" :name="card.name" :type="7" :key="index" v-for="(card, index) in cards7">
                            {{card.name}}
                        </card>
                    </div>
                    <div>
                        <card :index="index" :name="card.name" :type="8" :key="index" v-for="(card, index) in cards8">
                            {{card.name}}
                        </card>
                    </div>
                    <div>
                        <card :index="index" :name="card.name" :type="9" :key="index" v-for="(card, index) in cards9">
                            {{card.name}}
                        </card>
                    </div>
                </div>
                <div style="margin-left: 100px">
                    <label>发牌区</label>
                    <div>
                        <card :index="index" :name="card.name" :type="10" :key="index" v-for="(card, index) in cards10">
                            {{card.name}}
                        </card>
                    </div>
                    <label>弃牌区</label>
                    <div>
                        <card :index="index" :name="card.name" :type="11" :key="index" v-for="(card, index) in cards11">
                            {{card.name}}
                        </card>
                    </div>
                </div>
            </div>
            <button @click="resetMySelf" style="width: 80px; height: 30px; position: absolute; top:730px;">重置</button>
            <button @click="resetAll" style="width: 80px; height: 30px; position: absolute; top:800px;">重置全部</button>
        </main>
    </div>
</template>

<script>
  import Card from './Card'

  export default {
    name: 'landing-page',
    components: {Card},
    data () {
      return {
        cards: [{
          name: '',
          value: -1,
          position: 0
        }, {
          name: '',
          value: -1,
          position: 1
        }, {
          name: '',
          value: -1,
          position: 2
        }],
        cards2: [{
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }],
        cards3: [{
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }],
        cards4: [{
          name: '',
          value: -1,
          position: 0
        }, {
          name: '',
          value: -1,
          position: 1
        }, {
          name: '',
          value: -1,
          position: 2
        }],
        cards5: [{
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }],
        cards6: [{
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }],
        cards7: [{
          name: '',
          value: -1,
          position: 0
        }, {
          name: '',
          value: -1,
          position: 1
        }, {
          name: '',
          value: -1,
          position: 2
        }],
        cards8: [{
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }],
        cards9: [{
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }],
        cards10: [{
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }],
        cards11: [{
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }]
      }
    },
    methods: {
      resetLeft () {
        this.cards = [{
          name: '',
          value: -1,
          position: 0
        }, {
          name: '',
          value: -1,
          position: 1
        }, {
          name: '',
          value: -1,
          position: 2
        }]
        this.cards2 = [{
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }]
        this.cards3 = [{
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }]
      },
      resetRight () {
        this.cards4 = [{
          name: '',
          value: -1,
          position: 0
        }, {
          name: '',
          value: -1,
          position: 1
        }, {
          name: '',
          value: -1,
          position: 2
        }]
        this.cards5 = [{
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }]
        this.cards6 = [{
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }]
      },
      resetMySelf () {
        this.cards7 = [{
          name: '',
          value: -1,
          position: 0
        }, {
          name: '',
          value: -1,
          position: 1
        }, {
          name: '',
          value: -1,
          position: 2
        }]
        this.cards8 = [{
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }]
        this.cards9 = [{
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }]
        this.cards10 = [{
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }]
        this.cards11 = [{
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }]
      },
      resetAll () {
        this.cards = [{
          name: '',
          value: -1,
          position: 0
        }, {
          name: '',
          value: -1,
          position: 1
        }, {
          name: '',
          value: -1,
          position: 2
        }]
        this.cards2 = [{
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }]
        this.cards3 = [{
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }]
        this.cards4 = [{
          name: '',
          value: -1,
          position: 0
        }, {
          name: '',
          value: -1,
          position: 1
        }, {
          name: '',
          value: -1,
          position: 2
        }]
        this.cards5 = [{
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }]
        this.cards6 = [{
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }]
        this.cards7 = [{
          name: '',
          value: -1,
          position: 0
        }, {
          name: '',
          value: -1,
          position: 1
        }, {
          name: '',
          value: -1,
          position: 2
        }]
        this.cards8 = [{
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }]
        this.cards9 = [{
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }]
        this.cards10 = [{
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }]
        this.cards11 = [{
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }, {
          name: '',
          value: -1
        }]
      },
      onClick: function (value, index, type) {
        let list = []
        switch (type) {
          case 1:
            list = this.cards
            break
          case 2:
            list = this.cards2
            break
          case 3:
            list = this.cards3
            break
          case 4:
            list = this.cards4
            break
          case 5:
            list = this.cards5
            break
          case 6:
            list = this.cards6
            break
          case 7:
            list = this.cards7
            break
          case 8:
            list = this.cards8
            break
          case 9:
            list = this.cards9
            break
          case 10:
            list = this.cards10
            break
          case 11:
            list = this.cards11
            break
        }
        let card = list[index]
        // if (card.value === value.value) return
        card.value = value.value
        card.name = value.name
        list.sort((a, b) => {
          return b.value % 100 - a.value % 100
        })
      }
    }
  }
</script>

<style>
    @import url('https://fonts.googleapis.com/css?family=Source+Sans+Pro');

    * {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
    }

    body {
        font-family: 'Source Sans Pro', sans-serif;
    }

    #wrapper {
        background: radial-gradient(
                ellipse at top left,
                rgba(255, 255, 255, 1) 40%,
                rgba(229, 229, 229, .9) 100%
        );
        height: 100vh;
        padding: 60px 80px;
        width: 100vw;
    }

    #logo {
        height: auto;
        margin-bottom: 20px;
        width: 420px;
    }

    main {
        display: flex;
        justify-content: space-between;
    }

    main > div {
        flex-basis: 50%;
    }

    .left-side {
        display: flex;
        flex-direction: column;
    }

    .welcome {
        color: #555;
        font-size: 23px;
        margin-bottom: 10px;
    }

    .title {
        color: #2c3e50;
        font-size: 20px;
        font-weight: bold;
        margin-bottom: 6px;
    }

    .title.alt {
        font-size: 18px;
        margin-bottom: 10px;
    }

    .doc p {
        color: black;
        margin-bottom: 10px;
    }

    .doc card {
        font-size: .8em;
        cursor: pointer;
        outline: none;
        padding: 0.75em 2em;
        border-radius: 2em;
        display: inline-block;
        color: #fff;
        background-color: #4fc08d;
        transition: all 0.15s ease;
        box-sizing: border-box;
        border: 1px solid #4fc08d;
    }

    .doc card.alt {
        color: #42b983;
        background-color: transparent;
    }
</style>
