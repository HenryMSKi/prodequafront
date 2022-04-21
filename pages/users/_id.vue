<template>
  <div>
        <h1>Index Users</h1>
        <p>{{ $route.params }}</p>
  </div>
</template>

<script>
export default {
  validate(ruta){
    console.log(ruta.params.id)
    return /^\d+$/.test(ruta.params.id)
  }
};
</script>

<style>
</style>