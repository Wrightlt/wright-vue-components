<template>
  <div class="rows-text-dot" v-row-title>
    <!--Welcome to Wright's Vue Common Component Libraries  Welcome to Wright's Vue Common Component Libraries Welcome to Wright's Vue Common Component Libraries Welcome to Wright's Vue Common Component Libraries-->
    一棵开花的树 如何让你遇见我 在我最美丽的时刻为这 我已在佛前求了五百年 求它让我们结一段尘缘 佛于是把我化作一棵树 长在你必经的路旁 阳光下慎重地开满了花 朵朵都是我前世的盼望 当你走近请你细听 颤抖的叶是我等待的热情 而你终于无视地走过 在你身后落了一地的 朋友啊那不是花瓣 是我凋零的心
  </div>
</template>

<script>
  import Vue from 'vue'
  export default {
    name: 'RowsTextDot'
  }

  let getBLen = function(str) {
    if (str == null) return 0;
    if (typeof str != "string"){
      str += "";
    }
    return str.replace(/[^\x00-\xff]/g,"ab").length;
  }

  Vue.directive('row-title', {
    inserted: function (el, binding) {
      let n = el.offsetHeight
      let s = el.innerHTML
      for (let i = 0; i < s.length; i++) {
        el.innerHTML = s.substr(0, i)
        if (n < el.scrollHeight) {
          el.innerHTML = s.substr(0, i - 1)
          el.style.overflow = 'hidden'
          let lastChar = s.charAt(i - 1 - 1)
          // console.log('lastChar', lastChar)
          // console.log('binding', binding)
          let cutCharLength = 3
          if (isChinese(lastChar)) {
            cutCharLength = 2
          } else {
            cutCharLength = 3
          }
          el.innerHTML = s.substr(0, i - cutCharLength) + '...'
          break
        }
      }
    }
  })


  Vue.directive('max-byte', {
    inserted: function (el, binding) {
      let s = el.innerHTML
      let maxByte = binding.value
      let strByte = getBLen(s)
      console.log(' ')
      console.log('  ————————————')
      console.log('maxByte', maxByte)
      console.log('strByte', strByte)
      console.log('binding', binding)

      for (let i = 0; i < s.length; i++) {
        let currentStr = s.substr(0, i+1)
        let currentChar = s.charAt(i)
        el.innerHTML = currentStr
        let currentByte = getBLen(currentStr)
        console.log(' ')
        console.log('currentChar', currentChar)
        console.log('currentStr', currentStr)
        console.log('currentByte', currentByte)
        if (currentByte > maxByte) {
          let lastChar = currentChar
          console.log('lastChar', lastChar)
          let cutCharLength = 2
          if (getBLen(lastChar) > 1) {//是中文
            cutCharLength = 1
          } else {
            cutCharLength = 2
          }
          el.innerHTML = currentStr.substr(0, i-lastChar) + '...'
          break
        }
      }
    }
  })


  function isChinese(temp) {
    let re = /[^\u4e00-\u9fa5]/
    if (re.test(temp)) return false
    return true;
  }
</script>

<style rel="stylesheet" lang="scss" scoped>
  .rows-text-dot {
    text-align: justify;
    max-width: 300px;
    border: 1px solid red;
    max-height: calc(28px * 3);
    margin-bottom: 4px;
    font-size: 20px;
    line-height: 28px;
    font-weight: 700;
    overflow: hidden;
    word-break: break-all;
    /*word-break: break-word;*/
  }
</style>