<template>
  <div id="app">
    <header>
      <app-header/>
    </header>
    <main>
      <app-grid/>
    </main>
  </div>
</template>

<script>
import AppGrid from './components/AppGrid.vue';
import AppHeader from './components/AppHeader.vue';
export default{
  name:'app',
  components: {
    AppGrid ,
    AppHeader,
  },
}
</script>

<style lang="scss">
@import './style/general.scss';
header{
  background-color: $bg_header;
  height: 70px;
}
main{
  background-color: $bg_main;
  height: calc(100vh - 70px);
  overflow-y: auto;
}
span{
  margin-right: 4%;
}

</style>
