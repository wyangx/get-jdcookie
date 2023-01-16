<script setup lang="ts">
const CV = $ref('')
let CookieValue = $ref('')

const go = () => {
  if (CV) {
    const pin = CV.match(/pt_pin=.+?;/)
    const key = CV.match(/pt_key=.+?;/)
    if (pin && key) {
      CookieValue = pin[0] + key[0]
      if (navigator.clipboard)
        navigator.clipboard.writeText(CookieValue)
    }
  }
}
</script>

<template>
  <div>
    <div i-carbon-cookie text-4xl inline-block />
    <p>
      Get JDCookie
    </p>
    <p>
      <em text-sm op75>获取jd cookie</em>
    </p>

    <div py-4 />

    <input
      id="input"
      v-model="CV"
      placeholder="请粘贴完整的cookie"
      type="text"
      autocomplete="false"
      p="x-4 y-2"
      w="250px"
      text="center"
      bg="transparent"
      border="~ rounded gray-200 dark:gray-700"
      outline="none active:none"
      @keydown.enter="go"
    >

    <div min-h-6>
      {{ CookieValue }}
    </div>

    <div>
      <button
        class="m-3 text-sm btn"
        :disabled="!CV"
        @click="go"
      >
        Get
      </button>
    </div>
  </div>
</template>
