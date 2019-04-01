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
        cards: this.getDefaultList(3),
        cards2: this.getDefaultList(5),
        cards3: this.getDefaultList(5),
        cards4: this.getDefaultList(3),
        cards5: this.getDefaultList(5),
        cards6: this.getDefaultList(5),
        cards7: this.getDefaultList(3),
        cards8: this.getDefaultList(5),
        cards9: this.getDefaultList(5),
        cards10: this.getDefaultList(17),
        cards11: this.getDefaultList(4)
      }
    },
    methods: {
      getDefaultList (size) {
        let defaultList = []
        for (let i = 0; i < size; i++) {
          defaultList.push({
            name: '',
            value: -1
          })
        }
        return defaultList
      },
      resetLeft () {
        this.cards = this.getDefaultList(3)
        this.cards2 = this.getDefaultList(5)
        this.cards3 = this.getDefaultList(5)
      },
      resetRight () {
        this.cards4 = this.getDefaultList(3)
        this.cards5 = this.getDefaultList(5)
        this.cards6 = this.getDefaultList(5)
      },
      resetMySelf () {
        this.cards7 = this.getDefaultList(3)
        this.cards8 = this.getDefaultList(5)
        this.cards9 = this.getDefaultList(5)
        this.cards10 = this.getDefaultList(17)
        this.cards11 = this.getDefaultList(4)
      },
      resetAll () {
        // 左边
        this.resetLeft()
        // 右边
        this.resetRight()
        // 自己
        this.resetMySelf()
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
        if (this.isContainsClick(type, value.value)) return
        let card = list[index]
        card.value = value.value
        card.name = value.name
        list.sort((a, b) => {
          return b.value % 100 - a.value % 100
        })
        if (list[list.length - 1].value !== -1) {
          this.doSort(list, 0, 0)
        }
      },
      isContainsClick (type, value) { // 判断重复点击
        let bigList = []
        if (type < 4) {
          bigList = bigList.concat(this.cards).concat(this.cards2).concat(this.cards3)
        } else if (type < 7) {
          bigList = bigList.concat(this.cards4).concat(this.cards5).concat(this.cards6)
        } else if (type < 10) {
          bigList = bigList.concat(this.cards7).concat(this.cards8).concat(this.cards9)
        } else if (type === 10) {
          bigList = bigList.concat(this.cards10)
        } else {
          bigList = bigList.concat(this.cards11)
        }
        for (let i = 0; i < bigList.length; i++) {
          if (bigList[i].value === value) return true
        }
        return false
      },
      doSort (list, count, value) { // 把相同数向前排序
        let s = 0 // 相同项起始下标
        let c = 1 // 相同项个数
        for (let i = 0; i < list.length - 1; i++) {
          if (list[i].value % 100 !== list[i + 1].value % 100) {
            if (s > 0 && c > 1) {
              break
            }
            s = i + 1
            c = 1
          } else {
            c++
          }
        }
        let sameValue = 0
        if (s > 0 && c > 1) {
          const same = list.splice(s, c)
          sameValue = same[0].value
          if (count > c || (count === c && value > sameValue)) {
            list.splice(count, 0, ...same)
          } else {
            list.splice(0, 0, ...same)
          }
        }
        if (s + c !== list.length) {
          this.doSort(list, c, sameValue)
        }
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

    main {
        display: flex;
        justify-content: space-between;
    }

    main > div {
        flex-basis: 50%;
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
