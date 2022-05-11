<template>
<div class="row">
    <div class="col-12">
        <div class="input-group my-3">
            <input type="text" class="form-control" placeholder="Cerca Per Titolo" v-model="inputText" aria-label="Recipient's username" aria-describedby="button-addon2">
            <button @click="$emit('search', inputText)" class="btn btn-outline-secondary" type="button" id="button-addon2">Cerca</button>
        </div>
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