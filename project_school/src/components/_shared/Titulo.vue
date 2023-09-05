<template>
    <div class="containerTitle">
      <h1>{{ text }}</h1>
    </div>
</template>

<script>


    export default {
        props:{
            text: String
        }
    }
</script>

<style>

.containerTitle{
  display: flex;
  justify-content: center;
  align-items: center;
  color: rgb(147, 92, 173);
}

</style>