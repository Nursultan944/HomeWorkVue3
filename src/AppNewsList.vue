<template>
  <hr/>
  <h4>{{title}}</h4>
<ul>
  <li
    v-for="(item, idx) in news" :key="idx">
    {{ item.title }}
    <span v-if="item.wasRead">
      (Прочитано)
    </span>
  </li>
</ul>

</template>

<script>
export default {
  name: 'AppNewsList',
  inject: ['title', 'news']
}
</script>

<style scoped>

</style>
