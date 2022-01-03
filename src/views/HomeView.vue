<script setup>
import { ref } from 'vue'
import copy from 'copy-text-to-clipboard'

const url = ref('')
const adid = 18192

const result = ref('')
const format = () => {
  if(!url.value.includes('activity/')) return
  const u = url.value.replace('https://www.klook.com/zh-TW/activity/', '')
  const id = u.split('-')[0]
  result.value = `https://affiliate.klook.com/redirect?aid=${adid}&aff_adid=576626&k_site=https://www.klook.com/zh-TW/activity/${id}`
}

const clear = () => {
  url.value = ''
}
const copyText = () => {
  copy(result.value)
}
</script>

<template>
  <main class="mx-auto w-11/12 max-w-3xl">
    <section class="py-4">
      <div class="py-2">
        <input
          type="url"
          placeholder="https://www.klook.com/zh-TW/"
          v-model="url"
          class="text-xl w-full p-3 rounded-xl outline-none focus:ring-4 transition ring-lime-400"
        />
      </div>
      <div class="py-2">
        <input type="button" @click="format" value="轉換" class="btn bg-lime-500" />
      <input type="button" value="清除" @click="clear" class="btn bg-blue-500" />
      </div>
    </section>
    <section class="py-4">
      <div class="py-2">
        <input type="text" v-model="result" disabled class=" bg-gray-400 text-xl w-full p-3 rounded-xl outline-none" />
      </div>
      <div class="py-2">
        <input type="button" value="複製" @click="copyText" class="btn bg-indigo-500" />
        </div>
    </section>
  </main>
</template>
