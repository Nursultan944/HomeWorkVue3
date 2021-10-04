<template>
<div class="card">

<ul>
   <li v-for="(item,i) in 5" :key="i">
  <slot :iter="item" ></slot>
   </li>
</ul>

</div>
</template>

<script>
export default {
  name: 'AppList'
}
</script>

<style scoped>

</style>
