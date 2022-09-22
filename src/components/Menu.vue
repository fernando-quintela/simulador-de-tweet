<template>
  <nav class="navbar navbar-dark bg-primary">

    <div class="container">
      <span class="nacbar-brand fw-bold">Simulador de Tweets</span>

      <button class="btn pl-4 pr-4"
       @click="openCloseForm"
       :class="{ 'btn-success': !showForm, 'btn-danger': showForm}"
       >
       {{!showForm ? "Nuevo Tweet" :"Cerrar Tweet" }}
       </button>
    </div>

  </nav>
</template>

<script>
export default {
props: {
  showForm: Boolean,
  openCloseForm: Function,

}
};
</script>

<style>

</style>