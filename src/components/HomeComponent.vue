<template>
  <div>
    <div class="container-fluid gif">
             <!-- Vorrei mettere una gif netflix in background -->
    </div>
  </div>
</template>

<script>
export default {
name: 'HeaderComponent'
}
</script>

<style lang='scss'>
.gif{
    height: calc(100vh - 72px);
    background-image: url('/public/red-bg.gif');
    background-size: cover;
 }
</style>