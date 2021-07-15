<template>
  <div class="home">
    <h1 class="title"><a :href="link" target="_blank">Klook聯盟行銷網址</a></h1>
    <div class="card">
      <div class="row">
        <h2>填入聯合行銷ID(AID)</h2>
      </div>
      <div class="row">
        <input class="bar" type="number" v-model="aid" max="99999" min="10000" placeholder="填入聯合行銷ID(AID)">
      </div>
    </div>
    <div class="card">
      <div class="row">
        <h2>填入欲轉換網址</h2>
      </div>
      <div class="row">
        <input class="bar" type="text" v-model="target" placeholder="填入欲轉換網址">
      </div>
    </div>
    <div class="card">
      <div class="row">
        <div class="btn">
          <van-button type="primary" round @click="formateUrl">轉換</van-button>
        </div>
        <div class="btn">
          <van-button type="warning" round @click="target = ''">清除</van-button>
        </div>
      </div>
    </div>
    <div class="card">
      <div class="row">
        <input class="bar" type="text" placeholder="轉換網址" disabled :value="result">
      </div>
      <div class="row">
        <van-button type="primary" round @click="copyResult">複製</van-button>
      </div>
    </div>
  </div>
</template>

<script>
import copy from 'copy-text-to-clipboard'
import 'vant/lib/button/style'
import 'vant/lib/toast/style'
import { Button, Toast } from 'vant'
export default {
  name: 'Home',
  components: {
    [Button.name]: Button
  },
  data () {
    return {
      aid: 18191,
      target: '',
      result: '',
      link: 'https://affiliate.klook.com/redirect?aid=18191&aff_adid=548824&k_site=https%3a%2f%2fwww.klook.com%2fzh-TW%2f'
    }
  },
  methods: {
    copyResult () {
      copy(this.result)
      Toast.success('複製成功')
    },
    formateUrl () {
      const start = this.target.indexOf('activity/')
      if (start === -1) {
        Toast.fail('解析失敗')
        return
      }
      const activityId = this.target.substring(start + 9, start + 9 + 5)
      const url = `https://affiliate.klook.com/redirect?aid=${this.aid}&aff_adid=548832&k_site=https%3a%2f%2fwww.klook.com%2fzh-TW%2factivity%2F${activityId}-`
      this.result = url
    }
  }
}
</script>

<style lang="scss" scoped>
.home{
  width: 95%;
  margin: auto;
  max-width: 1200px;
  .title{
    text-align: center;
    font-size: 36px;
    line-height: 1.9;
    border-bottom: 1px solid #ccc;
  }
  .card{
    box-sizing: border-box;
    padding: 20px;
    .row{
      padding: 10px 10px;
      box-sizing: border-box;
      text-align: center;
      h2{
        font-size: 20px;
        line-height: 1.9;
      }
      .bar{
        font-size: 16px;
        line-height: 2;
        width: 100%;
        border: none;
        border-bottom: 1px solid #ccc;
      }
      .btn{
        display: inline-block;
        margin: 0 10px;
      }
    }
  }
}

</style>
