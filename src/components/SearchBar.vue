<template>
  <div class="col-6 g-0">
      <div class="input-group my-3" @keyup.enter="$emit('search', inputText)">
          <input type="text" class="form-control" placeholder="Cerca Per Titolo" v-model="inputText" aria-label="Recipient's username" aria-describedby="button-addon2">
          <button @click="$emit('search', inputText)" class="btn btn-outline-secondary" type="button" id="button-addon2"><i class="fa-solid fa-magnifying-glass"></i></button>
      </div>
  </div>
</template>

<script>
export default {
    name:'SearchBar',
    data(){
      return {
        inputText:'',
      }
    }
}
</script>

<style>

</style>