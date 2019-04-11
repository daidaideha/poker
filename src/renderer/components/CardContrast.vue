<script>
  let pokers1 = [[3, 111], [5, 111], [4, 111], [6, 111], [2, 111]]// 这是一个无序但连续且同花的二维结构数组
  let pokers2 = [[9, 111], [5, 222], [4, 444], [6, 333], [8, 111]]// 这是一个无序且不连续且不同花的二维结构数组
  let pokers3 = [[8, 111], [5, 222], [5, 444], [5, 333], [5, 111]]// 这是一个炸
  let pokers4 = [[10, 111], [5, 222], [2, 444], [2, 333], [5, 111]]// 这是一个两对

  // 判断是否顺子
  function isStraight (arrs) {
    arrs.sort(ascend)
    let first = arrs[0][0] // 取出第一个最小的数
    let index = 1// 从第二个开始索引
    while (arrs.length > index) {
      first++
      if (first !== arrs[index][0]) {
        // 如果不相等代表不连续
        return false
      }
      index++
    }
    return true
  }

  // 计算同花顺分数
  function GetFlushStraightScore (arrs) {
    arrs.sort(ascend)
    let first = arrs[0][0] // 取出第一个最小的数
    let index = 1// 从第二个开始索引
    while (arrs.length > index) {
      first++
      if (first !== arrs[index][0]) {
        // 如果不相等代表不连续
        return false
      }
      index++
    }
    return true
  }

  /* 判断是否为同花 */
  function isFlush (arrs) {
    let flower = arrs[0][1] // 取出第一个花
    let index = 1// 从第二个开始索引
    while (arrs.length > index) {
      if (flower !== arrs[index][1]) {
        // 如果不相等代表不是同花
        return false
      }
      index++
    }
    return true
  }

  /* 判断是否为num张相同 */
  function isSamePoker (arrs, num) {
    arrs.sort(ascend)
    let count = 1 // 计数
    let first = arrs[0][0] // 取出第一个最小的数
    let index = 1// 从第二个开始索引

    while (arrs.length > index) {
      if (first !== arrs[index][0]) {
        first = arrs[index][0]
        count = 1
      } else {
        count++
      }
      if (count === num) {
        return true
      }
      index++
    }
    return false
  }

  /* 判断是否为3带2 */
  function isFullHouse (arrs) {
    arrs.sort(ascend)
    let count = 1 // 计数器1
    let count2 = 1 // 计数器2
    let first = arrs[0][0] // 取出第一个最小的数
    let index = 1// 从第二个开始索引

    while (arrs.length > index) {
      if (first !== arrs[index][0]) {
        first = arrs[index][0]
        count2 = count
        count = 1
      } else {
        count++
      }
      index++
    }
    if ((count === 3 && count2 === 2) || (count === 2 && count2 === 3)) {
      return true
    }
    return false
  }

  function ascend (x, y) { // 按照数组的第1个值升序排列
    return x[0] - y[0]
}
  function descend (x, y) { // 按照数组的第1个值降序排列
    return y[0] - x[0]
}

  /* 判断是否为两对 */
  function isTwoPairs (arrs) {
    arrs.sort(ascend)
    let count = 1 // 计数器1
    let count2 = 1 // 计数器2
    let first = arrs[0][0] // 取出第一个最小的数
    let index = 1// 从第二个开始索引

    while (arrs.length > index) {
      if (first !== arrs[index][0]) {
        first = arrs[index][0]
        if (count === 2) {
          count2 = count
        }
        count = 1
      } else {
        count++
      }
      if (count === 2 && count2 === 2) {
        return true
      }
      index++
    }
    return false
  }

  // 计算高牌分数
  function GetSingleScore (arrs) {
    // arrs.sort(descend)
    let score = 0
    let first = arrs[0][0] // 取出第一个数
    let index = 0// 从第0个开始索引
    while (arrs.length > index) {
      score = score * 100 + arrs[index][0]
      index++
    }
    return score
  }

  // 计算一对分数
  function GetOnePairScore (arrs) {
    arrs.sort(ascend)
    let first = arrs[arrs.length][0] // 取出最大的数
    return first
  }

  function GetScore (arr) {
    let score = 0
    if (isFlush(arr) && isStraight(arr)) { // 同花顺
      score += 100000
    } else if (isSamePoker(arr, 4)) { // 四条
      score += 10000
    } else if (isFullHouse(arr)) { // 葫芦
      score += 10000
    } else if (isFlush(arr) && !isStraight(arr)) { // 同花
      score += 10000
    } else if (!isFlush(arr) && isStraight(arr)) { // 顺子
      score += 10000
    } else if (isSamePoker(arr, 3)) { // 三条
      score += 10000
    } else if (isTwoPairs(arr)) { // 两对
      score += 10000
    } else if (isSamePoker(arr)) { // 一对
      score += 10000
    } else { // 高牌
      score += 10000
    }
  }

  console.log(pokers4.sort(descend) + '<br>')
  let list = pokers4
  doSort(list.sort(descend), 0, 0)
  console.log(GetSingleScore(list))

  function contrast (arr1, arr2) {
    let point1 = 0
    let point2 = 0
    for (let i = 0; i < arr1; i++) {

    }
    for (let i = 0; i < arr2; i++) {

    }
  }

  function doSort (list, count, value) { // 把相同数向前排序
    let s = 0 // 相同项起始下标
    let c = 1 // 相同项个数
    let length = list.length - 1 // 填入的数据长度
    for (let i = 0; i < list.length - 1; i++) {
      if (list[i][0] === -1) { // 确定已经填入牌的长度
        length = i
        break
      }
      if (list[i][0] !== list[i + 1][0]) { // 当前牌和下一张牌不相同
        if (c > 1) { // 已经有相同的牌
          if (s > 0) { // 相同的牌不在数组最前方
            break
          } else {
            count = c
            value = list[i][0]
          }
        }
        s = i + 1 // 下移相同项起始项数
        c = 1 // 重置相同项个数
      } else { // 当前牌和下一张牌相同 相同数加1
        c++
      }
    }
    let sameValue = 0
    if (s > 0 && c > 1) {
      const same = list.splice(s, c)
      sameValue = same[0][0]
      if (count > c || (count === c && value > sameValue)) {
        list.splice(count, 0, ...same)
      } else {
        list.splice(0, 0, ...same)
      }
    }
    if (s + c < length) {
      doSort(list, c, sameValue)
    }
  }
</script>
