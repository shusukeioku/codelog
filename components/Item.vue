<template>
  <div 
    class="item w-full flex mx-auto p-5 cursor-pointer"
    @click="$router.push('/item/' + item.fields.slug)"
  >
    <div
      class="rounded-full border border-black text-center flex-shrink-0"
      style="width: 50px; height: 50px; padding: 14px 0;"
    >{{ item.fields.title[0] }}</div>
    <div class="ml-5">
      <h2 class="text-lg">{{ item.fields.title }}</h2>
      <p class="text-xs">{{ item.sys.updatedAt.slice(0,10) }}</p>
      <div
        v-if="item.fields.intro"
        class="text-xs intro" 
        v-html="$md.render(item.fields.intro)"
      ></div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['item']
}
</script>

<style lang="stylus">
.item
  transition all .3s ease-in-out
.item:hover
  background rgba(0,0,0,.1)
.intro
  code
    background #eee
    padding .2rem
    border-radius .2rem
</style>